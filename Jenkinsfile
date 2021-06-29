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
			withCredentials([string(credentialsId: 'Dockerhubpwd', variable: 'Dockerhubpwd')]){
			sh "docker login -u kishore121 -p ${Dockerhubpwd}"
			sh "docker push kishore121/nginxapp:${BUILD_NUMBER}"
			}
		     }
		}
	stage('Deploy Docker Image'){
		steps{
			sh "ssh ec2-user@52.41.20.24 'docker run -d -p 8082:80 --name nginxapp${BUILD_NUMBER} kishore121/nginxapp:${BUILD_NUMBER}'"
		     }
		}
	}
}
