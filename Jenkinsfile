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
                 dockerImage = docker.build("bihansoul/jenkins-cicd:$BUILD_NUMBER")
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
	  stage('display') { 
            steps { 
                 docker.withRegistry( '', 'dockerhub_access_token' ) {
				 dockerImage.push()
            }
      }
	  
    }
}