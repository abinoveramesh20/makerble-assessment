pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                // Install required packages
                sh 'apt-get update -qq && apt-get install -y build-essential nodejs'
            }
        }

        stage('Build') {
            steps {
                // Set up the working directory
                dir('app') {
                    // Install dependencies
                    sh 'bundle install'
                    // Copy all files to the app directory
                    sh 'cp -r $WORKSPACE/* .'
                }
            }
        }

        stage('Run Server') {
            steps {
                // Start the Rails server
                dir('app') {
                    sh 'rails server -b 0.0.0.0 &'
                }
            }
        }
    }

    post {
        always {
            // Cleanup or any post-processing steps can be added here
        }
    }
}
