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
                    sh 'bundle install'
                }
                sh 'cp -r * /app' // Copy files to app directory
            }
        }
        stage('Expose Port') {
            steps {
                sh 'docker run -p 3000:3000 ruby:3.1.2 rails server -b 0.0.0.0'
            }
        }
    }
}
