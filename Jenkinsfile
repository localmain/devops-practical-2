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
              
                sh 'docker build -t web:latest .' 
                sh 'docker tag web munna998/web:$BUILD_NUMBER'
               
          }
        }
  stage('Publish image to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'DockerHub', variable: 'abhi')]) {
                sh  'docker push munna998/web:$BUILD_NUMBER' 
		}
                  
          }
        }
		
    }
}
