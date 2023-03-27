pipeline {
  agent any

  tools {
    // Install the Maven version configured as "M2_HOME" and add it to the path.
    maven "M2_HOME"
	
  }
 

  stages {
    
  stage('GIT Clone') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'main']],
                 userRemoteConfigs: [[
                    url:  "https://github.com/PavanDeepakPagadala/PavanDevOpsProject.git",
                    credentialsId: '',
                 ]]
                ])
            }
        }
	stage('Build') {
	     steps {
	         sh "mvn clean  package"
	     }
	}
	stage('Test') {
	    steps {
	        sh "mvn clean verify -DskipITs=true',junit '**/target/surefire-reports/TEST-*.xml'archive 'target/*.jar"

	    }
	}

	

	
	//TO upload war file into S3 bucket using IAM role and S3Profile configuration in jenkins.
	 
  }

 

}
