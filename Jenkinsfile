pipeline {
    agent any
    stages {
        stage ('Build Docker Image'){
            steps{
                script{
                    dockerapp = docker.build("wmiyake/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }
        stage ('Push Docker Image'){
            script{
                docker.withRegistry('https://registry.hub.docker.com', 'dockerhub')
                dockerapp.push('latest')
                dockerapp.push("${env.BUILD_ID}")
            }
        }
    }
}