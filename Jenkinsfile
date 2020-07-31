pipeline {
 agent any
  stages {
    stage('SCM') {
      steps {
         git 'https://github.com/vpolice3/shopizer-2.12.0.git'
       }
    }
   stage("Build") {
	 def mvnHome = tool name:'Maven',type:'maven'
	sh ''' 
	      maven clean install
	      maven -B verify
	  '''
   }
   }
  }
}
