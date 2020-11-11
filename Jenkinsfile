pipeline {
    agent any

    environment {
        APP_ID = 'g-python'
    }

    stages {
        stage('Build') {
            steps {
                dir('packages') {
                    echo 'Building Python...'
                    sh '''
                        pip download -r ../requirements.txt
                    '''
                }
            }
        }
        stage('Sonatype Scan') {
            steps {
                dir('packages') {
                echo 'Scanning with Sonatype...'
                nexusPolicyEvaluation iqApplication: '${APP_ID}', iqStage: 'build', iqScanPatterns: [[scanPattern: 'image.tar']]
                
                //sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t build -i ${APP_ID} .'
                //sh 'java -jar ~/Sonatype/Apps/nxiq/nexus-iq-cli-*.jar -s http://localhost:8070 -a admin:admin123 -t stage-release -i ${APP_ID} .'
                
                }
            }
        }
    }
}
