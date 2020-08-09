pipeline {
 
  agent any
  stages{
    stage ('Build') {
      steps{
        echo "Building Project"
        sh 'mvn install -DskipTests=true'
      }
    }
    stage ('Archive') {
      steps{
        echo "Archiving Project"
        archiveArtifacts artifacts: '**/*.war', followSymlinks: false
      }
    }
   stage('Build images') {
	      steps {
		sh '''
			 
			  docker build -f "Dockerfile" -t vikaspolicedockerhub/shopizer-app:latest . 
		'''
	    }
    }
  }
}
