pipeline {
    agent any
    
    environment {
        APP_ID = 'g-php'
        COMPOSER = 'php -d memory_limit=-1 /usr/local/bin/composer.phar'
    }

    stages {
        stage('Build') {
            steps {
                sh '${COMPOSER} install'
            }
        }
        stage('Sonatype Scan') {
            steps {
                sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t release -i ${APP_ID} .'
            }
        }
    }
}
