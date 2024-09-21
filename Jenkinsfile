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
                dir('MyMvcApp') {
                    // Run tests
                    sh 'dotnet test'
                }
            }
        }
        stage('Publish') {
            steps {
                dir('MyMvcApp') {
                    // Publish the application
                    sh 'dotnet publish -c Release -o ./publish'
                }
        }
    }
        stage('Deploy to Local') {
            steps {
                script {
                    // Define the deployment directory
                    def deployDir = '/var/www/YourApp'

                    // Ensure the deployment directory exists
                    sh "mkdir -p ${deployDir}"

                    // Remove old files and copy published files
                    
                    sh "cp -r /var/lib/jenkins/workspace/Demo/MyMvcApp/publish/* ${deployDir}/"

                    // Optionally restart the application or service if it's running
                    // If you're using a systemd service:
                    sh "sudo systemctl restart MyMvcApp.service"  // Ensure your app service is properly configured
                }
            }
        }
}
}
