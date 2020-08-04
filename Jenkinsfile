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
			  docker build -f "Dockerfile" -t vikaspolicedockerhub/shopizer-app:latest .
			 
		  
		'''
	      }
       }
   stage('Push Image'){
	       steps{
	        withCredentials([string(credentialsId: 'DOCKER_HUB_CREDENTIALS', variable: '')]) {
		   bat "docker login -u dockerhandson -p ${DOCKER_HUB_CREDENTIALS}"  
		}
		   bat "docker push vikaspolicedockerhub/shopizer-app:latest"
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
