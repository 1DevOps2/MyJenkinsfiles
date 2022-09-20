pipeline {
    agent any
	environment {
  
   runSonarScan = true
   deployNexusArtifact = true
}
    stages {
	     stage('commit verification') {
            steps {
                sh '''#!/bin/bash
		res=$(git log -1 --pretty=%B)
                     if echo "$res" | grep -i ^build$; then
                      echo "Commit Matched -->  build=$res"
                      
                   else
                      echo "Commit not Matched -->  build=$res"
                      echo $res
		      
                      exit 1
                      
                   fi
		'''
            }
        }
	    
     
   
        stage('Deploy') {
		
		when { 
			expression { "$res" == 'build' }
		}
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
