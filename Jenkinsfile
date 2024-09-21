pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                     sh '''
                    # Deploy commands go here, for example:
                   cd /var/lib/jenkins/workspace/DotNetPipeline/MyMvcApp
                  echo "dayana123" |sudo dotnet build
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'echo "dayana123" |sudo dotnet test'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    sh 'echo "dayana123" |sudo dotnet publish  --output ./publish'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // You might want to run it in the background or on a specific port
                    sh 'echo "dayana123" |sudo dotnet ./publish/MyMvcApp.dll &'
                }
            }
        }

        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for more details.'
        }
    }

