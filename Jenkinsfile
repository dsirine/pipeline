pipeline {
  environment {
    registry = "dsirine/docker-test"
    registryCredential = 'dockerhub'
  }
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/dsirine/pipeline'
        sh 'npm install'
        sh 'npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
     
  }
}
