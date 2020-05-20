pipeline {
  agent any
  environment {
    APP_VERSION = '3.0'
    DOCKER_REGISTRY = 'bolfak'
    APP_NAME = 'nginxhello'
    dockerImage = ''
    registryCredentials = 'DockerHub'
  }
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build "${DOCKER_REGISTRY}/${APP_NAME}:${APP_VERSION}"
        }
      }
    }
    stage('Deploy Docker Image') {
      steps {
        script {
          docker.withRegistry( '', registryCredentials) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
