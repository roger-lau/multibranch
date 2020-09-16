pipeline {
    agent any
    
    environment {
        APP_ID = 'g-php'
    }

    stages {
        stage('Build') {
            steps {
                sh 'composer install'
            }
        }
        stage('Sonatype Scan') {
            steps {
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t release -i ${APP_ID} .'
            }
        }
    }
}
