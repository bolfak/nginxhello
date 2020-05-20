pipeline {
  agent any
  environment {
    APP_VERSION = '2.0'
    }
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t bolfak/nginxhello:${APP_VERSION} .'
      }
    }
    stage('Build with plugun') {
      steps {
        script {
          docker.build "bolfak/nginxhello:${APP_VERSION}"
        }
      }
    }
  }
}
