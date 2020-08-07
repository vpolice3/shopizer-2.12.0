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
            '''
        }
    }
   stage('Build images') {
	      steps {
		bat '''
			  cd sm-shop
			  docker build -f "Dockerfile" -t vikaspolicedockerhub/shopizer-app:latest .
			 
		  
		'''
	      }
       }
   stage('Push Image'){
	       steps{
	         withDockerRegistry([credentialsId: 'DOCKER_HUB_CREDENTIAL', url: '']) {
   			bat 'docker push vikaspolicedockerhub/shopizer-app:latest'
		 }
}
	       }
	  stage('Deploy to dev env') {
	      steps {
		bat '''
			  docker run -d --name=shopizer-app1 -p 8085:8080 vikaspolicedockerhub/shopizer-app:latest
			 
		  
		'''
	      }
       }
	 
}
}

