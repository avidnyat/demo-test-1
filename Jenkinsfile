node{
  def Namespace = "default"
  def ImageName = "avidnyat/webapp-color"
  def Creds	= "cc3561e8-4e36-4410-bcc9-2ade7dfaf569"
  try{

  stage('Docker Build, Push'){
    withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) {
      sh "docker build -t ${ImageName} ."
      sh "docker push ${ImageName}"
        }

    }
    
     } catch (err) {
      currentBuild.result = 'FAILURE'
    }
}
