pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/aditya-g18/Web_Application_Deployment.git'
      }
    }
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        echo 'Skipping tests for now...'
        // You can add test commands when you're ready to add them.
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t username/my-web-app .'
      }
    }
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
          sh 'docker push username/my-web-app'
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        echo 'Deploying to Kubernetes...'
      }
    }
  }
}
