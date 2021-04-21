pipeline {
    agent any

    environment {
        APP_ID = 'g-gradle'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building gradle...'
                sh 'gradle build'
            }
        }
        stage('Sonatype Scan') {
            steps {
                echo 'Scanning with Sonatype...'
                gradle nexusIQScan
            }
        }
    }
}
