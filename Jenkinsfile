pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'composer install'
            }
        }
        stage('Sonatype Scan') {
            steps {
                sh 'nxiq .'
            }
        }
    }
}
