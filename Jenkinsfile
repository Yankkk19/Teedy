pipeline {
  environment {
      registry = "yankkkkk/teedy_local:v1.0"
      registryCredential = 'docker_hub_id'
      dockerImage = 'teedy2024_manual'
  }
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
        script {
                  dockerImage = docker.build registry + ":$BUILD_NUMBER"
              }
      }
    }
    stage('Upload') {
      steps {
        script {
          docker.withRegistry( 'teedy2024_manual', registryCredential ) {
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
