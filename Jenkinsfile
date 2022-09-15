pipeline {

  environment {
    dockerimagename = "diepphamit/nodeapp"
    dockerImage = ""
  }

  agent any


  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/diepphamit/nodeapp_test.git'
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhublogin'
           }
      steps{
        script {
          docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push("latest")
          }
        }
      }
    }

  }

}
