pipeline {
    agent any
    stages{
	stage('Build'){
		steps{
			sh "docker build . -t kishore121/nginxapp:${BUILD_NUMBER}"
		     }
		}
	stage('Test'){
		steps{
			sh "echo "Testing" && sleep 20"
			
		     }
		}
	stage('Deploy'){
		steps{
			sh "echo "Deploying" && sleep 20"
		     }
		}
	}
}
