pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/mahesh-123123/docker1.git'
            }
        }
       /* stage('Maven Build') {
            steps {
                bat 'mvn clean'
                bat 'mvn install'
                bat 'mvn package'
            }
        }*/
        stage('Build Docker Image') {
            steps {
                script {
                  bat 'docker build -t maheshreddy123/pyt:v1 .'
                  bat 'docker run -itd -p 3030:80 maheshreddy123/pyt:v1'  
                 
                }
            }
        }
        
          stage('Deploy Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub',  url: '') {
                bat 'docker push maheshreddy123/pyt:v1'
               
                }
              }
            }
          }
        
        
    }
}
