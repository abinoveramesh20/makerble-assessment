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

    stage('Install kubectl') {
    steps {
        script {
            sh 'curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.29.0/bin/linux/amd64/kubectl'
            sh 'chmod +x kubectl'
            sh 'mv kubectl /path/to/jenkins/workspace/'
        }
    }
}


  stage('Deploy to Kubernetes') {
            steps {
                script {
                    // Your kubectl apply commands for deploying YAML files
                    sh 'kubectl apply -f namespace.yaml'
                    sh 'kubectl apply -f postgres-statefulset.yaml'
                    sh 'kubectl apply -f budget-app-deployment.yaml'
                    sh 'kubectl apply -f ingress.yaml'
                }
            }
  }
  }
}
