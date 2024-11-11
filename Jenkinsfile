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
        // Run your tests (e.g., npm test, pytest, etc.)
        sh 'npm test'  // Replace with your test command
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t username/my-web-app .'  // Replace username/my-web-app with your actual Docker image name
      }
    }
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
          sh 'docker push username/my-web-app'  // Replace username/my-web-app with your actual Docker image name
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        // Example of deploying to Kubernetes using kubectl
        sh 'kubectl apply -f k8s/deployment.yaml'  // Replace with your actual Kubernetes deployment YAML path
      }
    }
  }
}
