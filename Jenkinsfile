pipeline{

       agent any
       environment {
            DOCKERHUB_CREDENTIALS = 'docker-hub'
            IMAGE_NAME='pyflaskapp'
            IMAGE_TAG = 'v3'
       }

       stages{
        stage(Buid Docker Image ){
            steps{
                scripts{
               withCredentials([usernamePassword(credentialsId: DOCKERHUB_CREDENTIALS, usernameVariable: 'DOCKERHUB_USERNAME', 
passwordVariable: 'DOCKERHUB_PASSWORD')])
                sh "docker build -t ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG} ."
                sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
                sh "docker push index.docker.io/${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG}"
            } 

         }
      }
    }
  }