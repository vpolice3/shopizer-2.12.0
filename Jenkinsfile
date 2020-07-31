pipeline {
 agent any
  stages {
    stage('SCM') {
      steps {
         git 'https://github.com/vpolice3/shopizer-2.12.0.git'
       }
    }
   stage("Build") {
	    tools{
		  jdk 'jdk'
		  maven 'Maven'
	  }
     steps {
    bat ''' 
    	    mvn install -DskipTests=true
	        mvn clean install
      	    
       '''
   }
   }
  }
}
