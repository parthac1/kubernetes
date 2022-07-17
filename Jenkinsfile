 pipeline {
    agent any 
 tools {
  dockerTool 'jenkins-docker'
  maven 'jenkins-maven'
  git 'git'
  jdk 'my-jdk'
}

  stages {
     stage('build maven') {
        steps {
           sh 'mvn clean install package'
        }
     }

       stage('copy Artifact') {
        steps {
           sh 'cp -r target/*.jar docker'
        }
     }
  
       stage('build docker image') {
        steps {
           sh 'docker build . -t parthac1/myapp:v1'
        }
     }
  
        stage('docker push') {
        steps {
         withCredentials([string(credentialsId: 'Dockerpasword', variable: 'dockerpasword')]) {
         sh "docker login -u parthac1 -p ${dockerpasword}"
}
        }
        sh 'docker push parthac1/myapp:v1'
     
     }
  
  
  }
 
 
 
 
 
 }

