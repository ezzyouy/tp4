pipeline {
  environment {
    registry = "braezz/tp4_devops"
    registryCredential = 'dockerhub'
    dockerImage = 'b0b41c81-970f-443e-b9a6-5673b600cc69'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ezzyouy/tp4'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Publish Image') {
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