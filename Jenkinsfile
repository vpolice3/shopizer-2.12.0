pipeline {
 agent any
  stages {
    stage('SCM') {
      steps {
         git 'https://github.com/vpolice3/shopizer-2.12.0.git'
       }
    }
    stage('Build Projecct'){
            tools{
            jdk 'jdk'
            maven 'Maven'
        }
         steps{
            sh '''
              mvn clean install
              mvn clean package
            '''
        }
  }
}
