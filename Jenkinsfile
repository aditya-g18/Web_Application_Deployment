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
        sh 'npm install'  // Installs npm dependencies
      }
    }
    stage('Test') {
      steps {
        echo 'Skipping tests for now...'
        // Add test commands here when ready (e.g., npm test)
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t aditya1018/my-web-app .'  // Ensure this matches your actual Docker image name
      }
    }
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
          sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
          sh 'docker push aditya1018/my-web-app'  // Ensure this matches your Docker image name
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        echo 'Deploying to Kubernetes...'
        // Add Kubernetes deployment commands here
      }
    }
  }
}
