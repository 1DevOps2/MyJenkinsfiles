pipeline {
    agent any
	environment {
  		RELEASE_NOTES = sh (script: """git log -1 --pretty=format:%s""",  returnStdout:true)
		IAM_COMMIT = 'build' 
		runSonarScan = true
		deployNexusArtifact = true
}
	stages {
   
        stage('Deploy') {
		
		when { expression { "${RELEASE_NOTES}" == 'true' } }
            steps {
                echo 'Deploying...'
            }
        }
        
        stage('Testing') {
		when { expression { "${runSonarScan}" == 'true' } }
            steps {
                echo 'Testing...'
            }
        
    }
     
        stage('Maintaince') {
            steps {
                echo 'Maintaince..'
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
