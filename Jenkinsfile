pipeline {
    agent any
	environment {
  		RELEASE_NOTES = sh (script: """git log -1 --pretty=format:%s""",  returnStdout:true)
		IAM_COMMIT = 'build' 
		runSonarScan = true
		deployNexusArtifact = true
}
   
	    
	
   
        stage('Deploy') {
		
		when { expression { "${RELEASE_NOTES}" == 'build_CBI' } }
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
		 when { expression { "${deployNexusArtifact}" == 'true' } }
            steps {
                echo 'Releasing...'
            }
        }
	    
	}
   
}
