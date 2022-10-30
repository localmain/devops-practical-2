pipeline {
	agent { 
	   label "slave"
	}		

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/localmain/devops-practical-2.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t devops9class:latest .' 
                sh 'docker tag devops9class munna998/devops9class:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
      withCredentials([string(credentialsId: 'munna998', variable: 'DockerHub')]) {
           sh  'docker push munna998/devops9class:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
