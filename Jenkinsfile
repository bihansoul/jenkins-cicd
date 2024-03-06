pipeline {
   agent any
   stages {
      stage('clone') {
          steps {
              git 'https://github.com/bihansoul/jenkins-cicd.git'
          }
        }
	  stage('build') { 
            steps { 
                script{
                 app = docker.build("bihansoul/jenkins-cicd")
                }
            }
      }
	  stage('push') { 
            steps { 
				script{
                 docker.withRegistry( '', 'dockerhub_access_token' )
				 dockerImage.push()
                }
            }
      }
	  stage('display') { 
            steps { 
                 wrap([$class: 'BuildUser']) {
					sh 'echo "${BUILD_USER}"'
				}
            }
      }
	  
    }
}
