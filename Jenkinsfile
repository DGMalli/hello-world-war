pipeline {
    agent any	
	 
 stages {
      stage('checkout') {
           steps {             
                git branch: 'master', url: 'https://github.com/DGMalli/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
           steps {  
		 
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp dgmarjun/samplewebapp:latest' 
            }
        }

stage('Login to Docker hub') {
           steps {
              
                sh 'docker login --username=dgmarjun --password=Malli@1977'
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
       	  sh  'docker push dgmarjun/samplewebapp:latest'  
        }                 
          
        }     
      stage('Run Docker container on Jenkins Agent') {
             
            steps 
	      {
                sh "docker run -d -p 8003:8080 dgmarjun/samplewebapp:latest"
             }
        }
 
    }
	}
