pipeline {
    agent none	
	 
 stages {
      stage('checkout') {
	      agent {
               label "doc_node"
                    }
           steps {             
                git branch: 'master', url: 'https://github.com/DGMalli/hello-world-war.git'             
          }
        }       

  stage('Docker Build and Tag') {
	  agent {
               label "doc_node"
                    }
           steps {  
		 
                sh 'docker build -t samplewebapp:latest .' 
                sh 'docker tag samplewebapp dgmarjun/samplewebapp:latest' 
            }
        }

stage('Login to Docker hub') {
	agent {
              label "doc_node"
                    }
           steps {
              
                sh 'docker login --username=dgmarjun --password=Malli@1977'
          }
        }
     
  stage('Publish image to Docker Hub') {
	  agent {
               label "doc_node"
                    }
          
            steps {
       	  sh  'docker push dgmarjun/samplewebapp:latest'  
        }                 
          
        }     
   stage('Parallal execution'){
         parallel {
           stage('deploy on docker hub'){
                  agent {
                          label "doc_node"
                        }      
        
                 steps {
                sh 'docker run -d -p 8005:8080 dgmarjun/samplewebapp:latest'
             }
        }
                  stage('deploy on jenkins hub'){
                        agent {
                          label "new_slave"
                        }
        
                 steps {
                sh 'docker run -d -p 8124:8080 dgmarjun/samplewebapp:latest'
             }
        }
	 }
    }
	}
}
