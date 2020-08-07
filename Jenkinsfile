pipeline{
   agent any
   stages{
		stage('Build'){
			steps{
			  echo "Building Project"
			  sh './mvnw package'
			}
		}
		stage('Build'){
			steps{
			  echo "Archieve Project"
			  
			}
		}
		stage('Build'){
			steps{
			  echo "Docker Build Project"
			  
			}
		}
		stage('Build'){
			steps{
			  echo "Push to Docker Project"
			  
			}
		}
		stage('Build'){
			steps{
			  echo "Deploying to dev Env"
			  
			}
		}
	}    
}
