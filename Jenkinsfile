pipeline {
    agent any

    environment {
        APP_ID = 'g-ios'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building iOS...'
            }
        }
        stage('Sonatype Scan') {
            steps {
                echo 'Scanning with Sonatype...'
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t build -i ${APP_ID} .'
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t stage-release -i ${APP_ID} .'
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t release -i ${APP_ID} .'
                nexusPolicyEvaluation iqApplication: '${APP_ID}', iqStage: 'release'
            }
        }
    }
}
