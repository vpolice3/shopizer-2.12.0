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
			  docker build -f "Dockerfile.3.0.0" -t vikaspolicedockerhub/shopizer-app:latest .
			 
		  
		'''
	      }
       }
   stage('Push Image'){
	       steps{
	         withDockerRegistry([credentialsId: 'DOCKER_HUB_CREDENTIAL', url: '']) {
   			bat "docker push vikaspolicedockerhub/shopizer-app:latest"
		 }
}
	       }
   stage('Run image'){
    steps{
     bat '''
     cd sm-shop
     docker run vikaspolicedockerhub/shopizer-app:latest
     '''
   }
  }
}
}
