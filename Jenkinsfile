pipeline {
 agent any
 stages {
 stage('Build') { 
steps {
 sh 'mvn -B -DskipTests clean package' 
}
 }
 stage('K8s') {
 steps {
 sh 'kubectl set image deployments/hello-node teedy-local-v2gxl=yankkkkk/teedy_local:v1.0'
 }
 }
 }
 }
