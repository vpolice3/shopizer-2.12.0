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
            bat '''
              mvn clean install
              mvn clean package
            '''
        }
    }
   stage('Build images') {
	      steps {
		bat '''
			  cd sm-shop
			  docker build . -t shopizer-2.12.0
			 
		  
		'''
	      }
       }
   stage('Run image'){
    steps{
     bat '''
     cd sm-shop
     docker run shopizer-2.12.0
     '''
   }
  }
}
}
