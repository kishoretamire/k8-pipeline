pipeline {
    agent any
    stages{
	stage('Build Docker Image'){
		steps{
			sh "docker build . -t kishore121/nginxapp:${BUILD_NUMBER}"
		     }
		}
	stage('Image push'){
		steps{
			withCredentials([string(ccredentialsId: 'Dockerhubpwd', variable: 'Dockerhubpwd')]){
			sh "docker push -u kishore121 -p ${Dockerhubpwd} kishore121/nginxapp:${BUILD_NUMBER}"
			}
		     }
		}
	stage('Deploy DOcker Image'){
		steps{
			sh "ssh ec2-user@52.41.20.24 'docker run -d -p 80:80 --name nginxapp${BUILD_NUMBER} kishore121/nginxapp:${BUILD_NUMBER}'"
		     }
		}
	}
}
