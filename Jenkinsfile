pipeline {
    agent any
    
    environment {
        APP_ID = 'g-php'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building PHP...'
            }
        }
        stage('Sonatype Scan') {
            steps {
                echo 'Scanning with Sonatype...'
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t build -i ${APP_ID} .'
            }
        }
    }
}
