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
	    
	    
	    
	     stage('GEt Tag') {
		
            steps {
		    script {
			    

public class ProcessBuilderExample1 {

    public static void main(String[] args) {

        ProcessBuilder processBuilder = new ProcessBuilder();
        // Windows
        processBuilder.command("cmd.exe", "/c", "ping -n 3 google.com");

        try {

            Process process = processBuilder.start();

            BufferedReader reader =
                    new BufferedReader(new InputStreamReader(process.getInputStream()));

            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }

            int exitCode = process.waitFor();
            System.out.println("\nExited with error code : " + exitCode);

        } catch (IOException e) {
            e.printStackTrace();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

    }

}

		    }
            }
        }
     
   
        stage('Deploy') {
		
		when { 
			
			expression { "$proc" == 'build' }
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
