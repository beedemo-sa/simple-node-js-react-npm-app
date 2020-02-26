pipeline {
  agent {
    kubernetes {
      label 'node-alpine-pod'
      yamlFile 'node-pod.yaml'
    }
  }
  environment {
    CI = 'true'
  }
  stages {
    stage ('Build') {
      steps {
        container ('node6') {
          sh 'npm install'
        }
      }
    }
    stage ('Test') {
      steps {
        container ('node6') {
          sh './jenkins/scripts/test.sh'
        }
      }
    }
    stage ('Deliver') {
      steps {
        container ('node6') {
          sh './jenkins/scripts/deliver.sh'
          curl 'http://localhost:3000'
          input message: 'Finished using the web site? (Click "Proceed" to continue)'
        }
      }
    }
  }
}
