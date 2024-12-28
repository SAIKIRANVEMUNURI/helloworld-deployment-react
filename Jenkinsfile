pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository from GitHub
                git branch: 'main', url: 'https://github.com/SAIKIRANVEMUNURI/helloworld-deployment-react.git'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install npm dependencies using Windows batch commands
                bat 'npm install'
            }
        }
        
        stage('Build React App') {
            steps {
                // Build the React application using Windows batch commands
                bat 'npm run build'
            }
        }
        
        stage('Deploy to S3') {
            steps {
                // Deploy build files to the S3 bucket using AWS CLI
                bat '''
                aws s3 sync build s3://helloworld-deployment-react-bucket/ --delete
                '''
            }
        }
    }

    post {
        always {
            // Clean up the workspace after the build
            bat 'del /s /q build\\*'
        }
    }
}
