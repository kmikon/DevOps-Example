pipeline {
  agent {
    docker {
      image 'node:8-alpine'
      args '-p 3000:3000 --name Example'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Delivery') {
      steps {
        sh '''[ ! "$(docker ps -a | grep Example)" ] && docker container stop Example
[ ! "$(docker ps -a | grep Example)" ] && docker container rm Example
npm start'''
      }
    }
  }
}