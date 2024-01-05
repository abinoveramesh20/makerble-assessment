pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code repository
                git 'https://github.com/abinoveramesh20/makerble-assessment.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Docker images
                script {
                    docker.build('my-budget-app-image')
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run any tests if applicable
                // Example: docker.image('my-budget-app-image').inside {
                //     sh 'npm test' or any test command
                // }
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application using Docker Compose
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            // Clean up after the pipeline run (optional)
            script {
                sh 'docker-compose down'
            }
        }
    }
}
