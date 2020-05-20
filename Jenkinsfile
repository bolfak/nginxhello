pipeline {
  agent any
  environment {
    APP_VERSION = '${BUILD_NUMBER}'
    DOCKER_REGISTRY = 'bolfak'
    APP_NAME = 'nginxhello'
    DEPLOYMENT_NAME = 'nginxhello-test-deployment'
    CONTAINER_NAME = 'nginxhello-test'
    dockerImage = ''
    REGISTRY_CREDENTIALS = 'DockerHub'
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
          docker.withRegistry( '', REGISTRY_CREDENTIALS) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Deploy Latest image to cluster') {
      steps {
        script {
          sh 'kubectl set image deployment/${DEPLOYMENT_NAME} ${CONTAINER_NAME}=${DOCKER_REGISTRY}/${APP_NAME}:${APP_VERSION}'
        }
      }
    }
  }
}
