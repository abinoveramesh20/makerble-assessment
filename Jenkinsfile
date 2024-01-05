pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Check out the code from your repository
                    git 'https://github.com/abinoveramesh20/makerble-assessment.git' 
                    // Build the Docker image
                    sh 'docker-compose build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests if you have any
                    sh 'docker-compose run app rails test'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy the app using Docker Compose
                    sh 'docker-compose up -d'
                }
            }
        }
    }
}

