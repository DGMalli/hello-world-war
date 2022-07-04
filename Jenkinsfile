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
                sh 'sudo mv /home/slave_1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war /home/slave_1/workspace/HelloWorld_Pipeline/target/pipeline_project.war'
                sh 'sudo cp /home/slave_1/workspace/HelloWorld_Pipeline/target/pipeline_project.war /opt/apache-tomcat-9.0.64/webapps'
            }
        }
    }
}
