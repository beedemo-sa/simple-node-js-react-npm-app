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
  }
}
