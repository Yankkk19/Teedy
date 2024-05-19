pipeline {
  agent any
  stages {
    stage('Build') { 
      steps {
        sh 'sudo docker build -t teedy2024_manual .' 
      }
    }
    stage('Upload') {
      steps {
        sh 'sudo docker login  -u yankkkkk'
        sh 'dckr_pat_MXQycyw5fYlnleGaiELjkbznDd4'
        sh 'sudo docker tag teedy2024_manual yankkkkk/teedy_local:v1.0'
        sh 'sudo docker push yankkkkk/teedy_local:v1.0'
      }
    }
    stage('Run containers') {
      steps {
        sh ' sudo docker run -d -p 8084:8080 --name teedy_manual01 teedy2024_manual'
        sh '  sudo docker run -d -p 8082:8080 --name teedy_manual02 teedy2024_manual'
        sh ' sudo docker run -d -p 8083:8080 --name teedy_manual03 teedy2024_manual'
      }
    }
  }
}
