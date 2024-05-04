pipeline {
 agent any
 tools {
 maven 'Maven'
 }
 stages {
 stage('Build') {
 steps {
 script {
 bat "mvn clean package"
 }
 }
 post {
 success {
 echo "Archiving the Artifacts"
 archiveArtifacts artifacts: '**/target/*.war'
 }
 }
 }
 stage('Deploy to Tomcat') {
 steps {
 script {
deploy adapters: [tomcat9(credentialsId: '1f7801d1-3dc5-43e6-b0c4-5574088e1dc4', path: '', url: 'http://localhost:8080/')], contextPath: '/pipeline', war: '**/*.war'
 }
 }
 }
}
