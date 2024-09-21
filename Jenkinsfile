pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'cd MyMvcApp'
                    sh 'dotnet restore'
                    sh 'dotnet build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'dotnet test'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    sh 'dotnet publish  --output ./publish'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // You might want to run it in the background or on a specific port
                    sh 'dotnet ./publish/MyMvcApp.dll &'
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

