pipeline {
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
     
  }
}
