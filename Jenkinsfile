pipeline {
  agent {
    label "java"
  }
  stages {
    stage('checkout-scm') {
      steps{
        git branch: 'main', credentialsId: 'git-hub-pwd', url: 'https://github.com/divyaraniduggappa/javawebapp.git'
      }
    }
    
  }
}
