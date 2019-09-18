pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        nodejs('nodejs') {
          sh 'mkdir ~/.npm-global'
          sh 'npm config set prefix '~/.npm-global''
          sh 'export PATH=~/.npm-global/bin:$PATH'
          sh 'source ~/.profile'
          sh 'npm install'
        }

      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh '''./jenkins/scripts/deliver.sh
./jenkins/scripts/kill.sh'''
      }
    }
  }
  environment {
    CI = 'true'
  }
}
