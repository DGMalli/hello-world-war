 
pipeline {
    agent { label 'java' }
   
      
    stages {       
          
        stage('Clone Project') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/DGMalli/hello-world-war.git'
            }
        }
         stage('Build Project') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                 sh 'sudo cp /home/slave_1/workspace/Multi_master/target/hello-world-war-1.0.0.war /opt/apache-tomcat-9.0.64/webapps'
            }
        }
    }
}
