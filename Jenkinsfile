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
     stage ('Build jar') {
            steps {
                sh 'mvn clean install' 
            }
            }
    stage('Building image') {
      steps{
        script {
          dockerImage =  docker.build("ajayk333/spring-boot-docker-demo")
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