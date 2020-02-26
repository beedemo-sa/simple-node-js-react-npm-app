pipeline {
  agent {
    kubernetes {
      label 'node-alpine-pod'
      yamlFile 'node-pod.yaml'
    }
  }
  stages {
    stage ('Build') {
      steps {
        container ('node6') {
          sh 'npm install'
        }
      }
    }
  }
}
