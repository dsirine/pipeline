node{
  def Namespace = "default"
  def ImageName = "dsirine/docker-test"
  def Creds	= "dockerhub"
  try{
    stage('Checkout'){
      git(url: "https://github.com/dsirine/pipeline.git")
    } 
    stage('RUN Unit Tests'){
      sh "npm install"
      sh "npm test"
    }
    stage('Docker Build') {
      sh "docker build -t ${ImageName}:${imageTag} ."
    }
    stage('Scan docker image') {
      aquaMicroscanner imageName: "${ImageName}:${imageTag}", notCompliesCmd: 'exit 1', onDisallowed: 'fail'
    }
    stage('Docker Build, Push'){
      withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) {        
        sh "docker push ${ImageName}"
      }
    }    
  } catch (err) {
    currentBuild.result = 'FAILURE'
  }
}
