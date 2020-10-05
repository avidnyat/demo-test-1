pipeline {
  agent any
  def Namespace = "default"
  def ImageName = "avidnyat/webapp-color"
  def Creds = "cc3561e8-4e36-4410-bcc9-2ade7dfaf569"
  try{
    stages {
        stage('Build') {
            stages {
               stage("repo checkout") {
                   steps {
                      echo "Checking out repo"
                      sh "sudo ansible-playbook /home/ubuntu/ansible/git-clone.yml -l web_server -u root --extra-vars \"version=${env.BUILD_NUMBER}\""
                   }
               }
               stage("build image and push") {
                   steps {
                      echo "Building Image"
                      sh "sudo ansible-playbook /home/ubuntu/ansible/build-image.yml -l web_server -u root  --extra-vars \"version=${env.BUILD_NUMBER}\""
                      echo "Pushing Image"
                      sh "docker push ${ImageName}"
                   }
               }
               
            }
        }
        
      }
    } catch (err) {
      currentBuild.result = 'FAILURE'
    }
}