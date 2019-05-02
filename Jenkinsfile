pipeline {
  agent none 
  stages {
    stage('Check Docker') {
        agent any 
        steps {
            echo 'Hello, Maven'
            sh 'mvn --version'
        }
    }

  stage('Docker') {
      agent {
        docker {
          image 'node:8-alpine'
          args '-p 3000:3000 --name Docker_example'
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
            sh 'npm start'
          }
        }
      }
    }
  }
}