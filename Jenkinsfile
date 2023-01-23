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
    stage('build') {
      steps{
         sh 'mvn clean install' 
      }
    }
  }
}
