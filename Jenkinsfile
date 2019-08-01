pipeline {
  environment {
    registry = "dsirine/docker-test"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
  tools {nodejs "node" }
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/dsirine/pipeline'
      }
    }
    stage('Build') {
       steps {
         sh 'npm install'
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          sh "docker build -t ${dockerImage}:${imageTag} ."
        }
      }
    }
    stage('Deploy Image'){
      withDockerRegistry([credentialsId: "${registryCredential}", url: 'https://index.docker.io/v1/']) {        
        sh "docker push ${dockerImage}"
      }
    } 
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
