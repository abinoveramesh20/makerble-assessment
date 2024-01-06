pipeline {
    agent {
        docker {
            image 'ruby:3.1.2'  // Use the specified Ruby image
            args '-u root'      // Run as root to avoid permission issues
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'apt-get update -qq && apt-get install -y build-essential nodejs'
                sh 'mkdir /app'
                copyRecursive('Gemfile', 'Gemfile.lock', '/app/')  // Copy Gemfiles
                sh 'cd /app && bundle install'
                copyRecursive('.', '/app/')  // Copy all other project files
            }
        }

        stage('Test') {
            steps {
                sh 'cd /app && bundle exec rspec'  // Adapt to your test command
            }
        }
    }
}
