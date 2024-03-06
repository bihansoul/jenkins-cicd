pipeline {
   agent any
   stages {
      stage('clone') {
          steps {
              git 'https://github.com/bihansoul/jenkins-cicd.git'
          }
        }
	  stage('Build') { 
            steps { 
                script{
                 app = docker.build("jenkins-cicd-image")
                }
            }
        }
    }
}