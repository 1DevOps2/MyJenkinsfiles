pipeline {
    agent any
	environment {
   checkoutCode = true
   runSonarScan = true
   deployNexusArtifact = true
}
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
   
        stage('Deploy') {
		when { expression { "${checkoutCode}" == 'true' } }
            steps {
                echo 'Deploying...'
            }
        }
        
        stage('Testing') {
		when { expression { "${runSonarScan}" == 'false' } }
            steps {
                echo 'Testing...'
            }
        
    }
     
        stage('Maintaince') {
            steps {
                echo 'Maintaince...'
            }
        }
	    
	 stage('Release') {
		 when { expression { "${deployNexusArtifact}" == 'false' } }
            steps {
                echo 'Releasing...'
            }
        }
	    
	}
   
}
