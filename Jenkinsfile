pipeline {
  agent any
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
                   }
               }
               
           
        
        
      }
  }