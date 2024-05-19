pipeline {
  agent any
  stages {
    stage('Package') { 
      steps {
        checkout scmGit(branches: [[name: '*/master']], extensions: [], 
userRemoteConfigs: [[url: 'https://github.com/Yankkk19/Teedy.git']])
        sh 'mvn -B -DskipTests clean package' 
      }
    }
    stage('Build') { 
      steps {
        sh 'docker build -t teedy2024_manual .' 
      }
    }
    stage('Upload') {
      steps {
        sh 'docker login  -u yankkkkk -p Jylshizhu506037@'
        sh 'docker tag teedy2024_manual yankkkkk/teedy_local:v1.0'
        sh 'docker push yankkkkk/teedy_local:v1.0'
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
