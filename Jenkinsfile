pipeline {
    agent any 
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
    }
}
