pipeline {
 
  agent any
  stages{
    stage ('Build') {
      tools{
            jdk 'jdk'
            maven 'Maven'
        }
      steps{
        echo "Building Project"
        sh './mvnw clean package'
      }
    }
  }
}	
