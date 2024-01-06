pipeline {
    agent {
        docker {
            image 'ruby:3.1.2'
            args '-u root'
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'apt-get update -qq && apt-get install -y build-essential nodejs'
                sh 'mkdir /app'
                sh 'cp Gemfile Gemfile.lock /app/'  // Copy Gemfiles
                sh 'cd /app && bundle install'
                sh 'cp -r * /app/'  // Copy all other project files
            }
        }

    }
}
