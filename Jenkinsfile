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
 sh 'kubectl set image deployments/hello-node teedy-local-6w6rf=yankkkkk/teedy_local:v1.0'
 }
 }
 }
 }
