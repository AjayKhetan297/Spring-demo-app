pipeline {
  environment {
    registry = "gustavoapolinario/docker-test"
    registryCredential = 'docker-hub'
    dockerImage = ''
  }
  agent any
  tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/AjayKhetan297/Spring-demo-app.git'
      }
    }
     stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
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