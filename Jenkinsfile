pipeline {
  agent {
    label "java"
        }
  environment{
    PATH = "/home/jenkins/apache-maven-3.8.7/bin:$PATH"
             }
  stages {
    stage('checkout-scm') {
      steps{
        git branch: 'main', credentialsId: 'git-hub-pwd', url: 'https://github.com/divyaraniduggappa/javawebapp.git'
           }
        }
    stage('build on maven') {
      steps{
         sh 'mvn clean install' 
           }
        }
    stage('deploy on tomcat') {
      steps{   
        sshagent(['ubuntu-Tomcat-privatekey']) { 
        sh "scp -o StrictHostKeyChecking=no /home/jenkins/workspace/Javawebapp-tomcat/target/SimpleWebApplication.war ubuntu@13.233.143.78:/opt/tomcat/apache-tomcat-9.0.71/webapps"        
        }
           }
       }
  }
  
  post{
    sucess{
      emailext attachLog: true,
               to: "divyarani0911@gmail.com, kavyasrinigowda@gmail.com",
               subject: "Jenkins-Build: ${currentBuild.currentResult}",
               body: "Project Name: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}\nBuild Status: ${currentBuild.currentResult}"
        
          }
    failure{
      emailext attachLog: true,
               to: "divyarani0911@gmail.com, kavyasrinigowda@gmail.com",
               subject: "Jenkins-Build: ${currentBuild.currentResult}",
               body: "Project Name: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}\nBuild Status: ${currentBuild.currentResult}\nMore can be found here:${env.BUILD_URL}"
         
           }
    }
  
}
