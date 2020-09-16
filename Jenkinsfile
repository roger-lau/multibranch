pipeline {
    agent any
    
    triggers {
        pollSCM('') // Enabling being build on Push
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building.. iOS (Triggered)'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
