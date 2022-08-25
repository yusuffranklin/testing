pipeline {
  agent any
    
  tools {nodejs "node"}

  environment{
  	dockerhub=credentials('dockerhub')
  }
    
  stages {
        
    stage('Git') {
      steps {
        git 'https://github.com/yusuffranklin/testing.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
         sh '<<Build Command>>'
      }
    }  
    
    stage('Test') {
      steps {
        sh 'node test'
      }
    }

    stage("Docker build"){
      steps{
        sh 'docker version'
        sh 'docker build -t yusuffranklin/project:0.1 .'
        sh 'docker image list'
      }
    }

    stage("Push Image to Docker Hub"){
      steps{
        sh 'docker login -u yusuffranklin -p JFkenedy@911'
        sh 'docker push  yusuffranklin/project:0.1'
      }
    }
  }
}
