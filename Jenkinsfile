pipeline {
    
    agent any 
    
    environment {
        DOCKER_HUB_CREDENTIALS = 'docker-hub-token'
        DOCKER_IMAGE_NAME = 'packetcodeofficial/angular-app'
        DOCKER_IMAGE_TAG = "${env.BUILD_NUMBER}"
    }
    
    stages {
        
        stage('Checkout'){
           steps {
                git branch: 'main',
                url: 'https://github.com/packetcode/docker-crash-course'
           }
        }

        stage('Build Docker'){
            steps{
                script{
                    sh '''
                    echo 'Buid Docker Image'
                    docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG} .
                    '''
                }
            }
        }

        stage('Push the artifacts'){
           steps{
                script{
                   withCredentials([string(credentialsId: DOCKER_HUB_CREDENTIALS, variable: 'DOCKER_HUB_TOKEN')]) {
                        sh "docker login -u kamaltejag -p ${DOCKER_HUB_TOKEN}"

                        // Push the Docker image to Docker Hub
                        sh "docker push ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                    }
                }
            }
        }
    }
}