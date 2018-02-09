pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }
    
  }
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'echo Built'
          }
        }
        stage('error') {
          steps {
            echo 'Side work'
          }
        }
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh 'echo Tested'
      }
    }
    stage('Deliver') {
      steps {
        sh '''#./jenkins/scripts/deliver.sh
echo Delivering'''
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh '''#./jenkins/scripts/kill.sh
echo Delivered'''
      }
    }
  }
  environment {
    e2 = 'v2'
  }
}