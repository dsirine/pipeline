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
          sh "docker build -t ${ImageName}:${imageTag} ."
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
           docker.withRegistry( '', registryCredential ) {
           sh "docker push ${ImageName}"
           }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
