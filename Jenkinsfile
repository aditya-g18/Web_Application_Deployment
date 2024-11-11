pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/aditya-g18/Web_Application_Deployment.git'
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
        sh 'docker build -t your-username/my-web-app .'  // Replace with your actual Docker image name
      }
    }
    stage('Push to Docker Hub') {
      steps {
        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
        sh 'docker push your-username/my-web-app'  // Replace with your Docker image name
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
