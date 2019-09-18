pipeline {
  agent {
    docker {
      image 'node:6-apline'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm -v'
      }
    }
    stage('Test') {
      steps {
        sh 'echo "hello world"'
      }
    }
    stage('Deploy ') {
      steps {
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    Ci = 'true'
  }
}