pipeline {
    agent any 

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/GitHubDayana/DemoRepo.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'cd MyMvcApp'
                    sh 'dotnet restore'
                    sh 'dotnet build --configuration Release'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh 'dotnet test --no-build --configuration Release'
                }
            }
        }

        stage('Publish') {
            steps {
                script {
                    sh 'dotnet publish --configuration Release --output ./publish'
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

