pipeline {
	environment {
	registry = "bihansoul/jenkins-cicd"
	registryCredential = 'dockerhub_username_password'
	dockerImage = ''
	}
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
						dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
      }
	  stage('push') { 
            steps { 
				script{
						docker.withRegistry('', registryCredential) {
						dockerImage.push()
					}
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
	  stage('Deploy') {
			steps {
				script {
					input message: 'Xác nhận triển khai?',
					submitter: 'user'
				}
		  }
	  }
	  
    }
}
