pipeline {
    agent {
        docker {
            image 'ruby:3.1.2'
            args '-v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'apt-get update -qq && apt-get install -y build-essential nodejs'
            }
        }
        stage('Setup and Build') {
            steps {
                dir('app') {
                    // Install dependencies within the app directory
                    sh 'bundle install'
                    // Copy the rest of the files to the app directory
                    sh 'cp -r $WORKSPACE/* .'
                }
            }
        }
        stage('Expose Port') {
            steps {
                dir('app') {
                    // Start the Rails server within the app directory
                    sh 'rails server -b 0.0.0.0'
                }
            }
        }
    }
}
