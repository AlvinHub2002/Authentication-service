pipeline {	
	agent any	tools {	    
		maven 'my-maven’		
		jdk 'my-jdk’	
	}	
	stages {        
		stage('Clone'){			
			steps {git url:'https://github.com/sep-2024-trivandrum/authentication-service.git', branch:'main’}			}		
		stage('Build'){			
			steps {sh "mvn clean install -DskipTests"}		
		}		
		stage('Test'){			
			steps{sh "mvn test"}		}		
		}
		stage('Deploy') {			
			steps { sh "docker build -t auth-image ."			    
			            sh "docker run -p 8090:8090 -d --name auth-container auth-image"}		
		}		
	}
}
