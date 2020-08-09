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
              
              mvn clean install -DskipTests=true
            '''
        }
    }
   stage('Build images') {
	      steps {
		sh '''
			 
			  docker build -f "Dockerfile" -t vikaspolicedockerhub/shopizer-app:latest .
			 
		  
		'''
	      }
       }
   stage('Push Image'){
	       steps{
	         withDockerRegistry([credentialsId: 'DOCKER_HUB_CREDENTIALS', url: '']) {
   			sh 'docker push vikaspolicedockerhub/shopizer-app:latest'
		 }
}
	       }
	  stage('Deploy to dev env') {
	      steps {
		sh '''
			  docker rm -f shopizer-appication1 || true
			 docker run -d --name=shopizer-appication1 -p 8081:8080 vikaspolicedockerhub/shopizer-app:latest
			 
		  
		'''
	      }
       }
	 
}
}

