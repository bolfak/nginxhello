pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Build Docker Imagesh') {
      steps {
        sh 'docker build -t bolfak/nginxhello .'
        }
      }
    }
  }
}
