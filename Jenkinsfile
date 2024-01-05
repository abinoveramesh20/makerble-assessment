pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/abinoveramesh20/makerble-assessment.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    docker.build('my-budget-app-image')
                }
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests if applicable
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    post {
        always {
            script {
                sh 'docker-compose down'
            }
        }
    }
}
