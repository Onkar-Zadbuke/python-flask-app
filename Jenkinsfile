pipeline{

       agent any
       environment {
            DOCKERHUB_CREDENTIALS = 'docker-hub'
            IMAGE_NAME='pyflaskapp'
            IMAGE_TAG = 'v3'
       }
  stages {
          stage('Build the Image') {
              steps {
                script {
                  withCredentials([usernamePassword(credentialsId: DOCKERHUB_CREDENTIALS, usernameVariable: 'DOCKERHUB_USERNAME', 
passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        sh "docker build -t ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }     
        }
   }    
        stage('Login to docker & Push it') {
            steps {
                script {
                        sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
                        sh "docker push index.docker.io/${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG}"
                        }        
                  }
            }
        }   
<<<<<<< HEAD
    } 
=======

>>>>>>> 69928ecafb3bcde1df6317201d9fbe4ec8cae82e
