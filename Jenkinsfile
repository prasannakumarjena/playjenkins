pipeline {
     environment {
    registry = "pkjdocker/jenkinstest"
  }
  agent any
  stages {
    stage('Checkout Source') {
      steps {
        git 'https://github.com/prasannakumarjena/playjenkins'
      }
    }
    stage{
        steps{
            script {
              docker.build registry + ":$BUILD_NUMBER"
            }
        }
    }
  }
}
