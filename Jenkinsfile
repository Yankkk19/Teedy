pipeline {
 agent any
 stages {
 stage('Build') { 
steps {
 bat 'mvn -B -DskipTests clean package' 
}
 }
 stage('pmd') {
 steps {
 bat 'mvn pmd:pmd'
 }
 }
   stage('test report') {
 steps {
 bat 'mvn jacoco:report'
 }
 }
 }
 post {
 always {
 archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
 archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
 archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
 }
 }
 }
