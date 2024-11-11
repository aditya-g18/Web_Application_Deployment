pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/your-username/your-repository.git'
      }
    }
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        // Add your tests here (e.g., npm test)
        echo 'Running tests...'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t your-username/my-web-app .'
      }
    }
    stage('Push to Docker Hub') {
      steps {
        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
        sh 'docker push your-username/my-web-app'
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        // This will be handled later by Kubernetes deployment
        echo 'Deploying to Kubernetes...'
      }
    }
  }
}
