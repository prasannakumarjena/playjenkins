pipeline {
     environment {
     registry = "pkjdocker/jenkinstest"
     registryCredential = 'dockerhub'
     dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/prasannakumarjena/playjenkins'
      }
    }
    stage('docker image build'){
        steps{
            script {
              dockerImage = docker.build registry + ":$BUILD_NUMBER"
              sh "docker images"
            }
        }
    }
    stage('Docker Image push') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
