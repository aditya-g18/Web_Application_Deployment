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
        sh 'npm install'  // Adjust this if you're using a different build tool (e.g., for Python, Maven, etc.)
      }
    }
    stage('Test') {
      steps {
        // Add your tests here (e.g., npm test, pytest, etc.)
        echo 'Running tests...'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t aditya1018/my-web-app .'  // Replace aditya1018/my-web-app with your actual Docker image name
      }
    }
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
          sh 'docker push aditya1018/my-web-app'  // Replace aditya1018/my-web-app with your actual Docker image name
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        // Deployment to Kubernetes will be handled by Kubernetes deployment YAML files
        echo 'Deploying to Kubernetes...'
      }
    }
  }
}
