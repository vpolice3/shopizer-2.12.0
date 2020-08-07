pipeline {
 
  agent any
  stages{
    stage ('Build') {
      tools{
            jdk 'JAVA_HOME'
            maven 'Maven'
        }
      steps{
        echo "Building Project"
        sh 'mvn clean install'
      }
    }
  }
}	
