pipeline {
 agent any
  stages {
	  tools{
		  jdk 'jdk'
		  maven 'Maven'
    stage('SCM') {
      steps {
         git 'https://github.com/vpolice3/shopizer-2.12.0.git'
       }
    }
   stage("Build") {
     steps {
    bat ''' 
    	    mvn install -DskipTests=true
	        mvn clean install
      	    
       '''
   }
   }
  }
}
