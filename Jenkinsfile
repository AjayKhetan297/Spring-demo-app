pipeline {
  environment {
    registry = "gustavoapolinario/docker-test"
    registryCredential = 'docker-hub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/AjayKhetan297/Spring-demo-app.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage =  docker.build("ajayk333/demo-spring")
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}