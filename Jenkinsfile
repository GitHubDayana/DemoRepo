pipeline {
    agent any 
    stages {
        stage('Clone Repository') {
            steps {
                // Clone the Git repository
                git url: 'https://github.com/GitHubDayana/DemoRepo.git', branch: 'main'
            }
        }
         stage('Build') {
            steps {
                // Navigate to the project directory if necessary
                sh 'cd MyMvcApp'
                dir('MyMvcApp') {  // Adjust if your .NET project is in a subdirectory
                    // Build the .NET application
                    sh 'dotnet build'
                }
            }
        }
        stage('Test') {
            steps {
                // Your test steps here
                echo 'Testing...'
            }
        }
    }
}

