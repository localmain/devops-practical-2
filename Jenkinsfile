pipeline {
	agent any		

 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/localmain/devops-practical-2.git'
             
          }
        }
       

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t dev:latest .' 
                sh 'docker tag dev munna998/dev:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
		    withDockerRegistry(credentialsId: "DockerHub"uu, url: "" ]) {
                    sh  'docker push munna998/dev:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
