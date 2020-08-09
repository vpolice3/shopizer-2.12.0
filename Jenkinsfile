pipeline {
  environment {
    registry = "vikaspolicedockerhub/shopizer-app"
    registryCredential = 'DOCKER_HUB_CREDNTIALS'
    dockerImage = ''
  }
  agent any
  stages{
    stage ('Build') {
      steps{
        echo "Building Project"
        sh 'mvn install -DskipTests=true'
      }
    }
  }
}
