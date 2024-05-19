pipeline {
  environment {
      registry = "YourDockerhubAccount/YourRepository"
      registryCredential = 'dockerhub_id'
      dockerImage = ''
  }
  agent any
  stages {
    stage('Building our image') {
          steps {
              script {
                  dockerImage = docker.build registry + ":$BUILD_NUMBER"
              }
          }
      }
      stage('Deploy our image') {
          steps {
              script {
                  docker.withRegistry( '', registryCredential ) {
                      dockerImage.push()
                  }
              }
          }
      }
    stage('Run containers') {
      steps {
        sh ' docker run -d -p 8084:8080 --name teedy_manual01 teedy2024_manual'
        sh '  docker run -d -p 8082:8080 --name teedy_manual02 teedy2024_manual'
        sh ' docker run -d -p 8083:8080 --name teedy_manual03 teedy2024_manual'
      }
    }
  }
}
