pipeline{

       agent any
       environment {
            DOCKERHUB_CREDENTIALS= 'docker-hub'
            IMAGE_NAME='pyflaskapp'
            IMAGE_TAG = 'v3'
       }
  stages {
          stage('Build and Push Docker Image') {
              steps {
                script {
                  withCredentials([usernamePassword(
                    credentialsId: DOCKERHUB_CREDENTIALS, 
                    usernameVariable: 'DOCKERHUB_USERNAME', 
                    passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                        
                        sh "docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PASSWORD}"
                        echo 'successfully logged In'

                        sh "docker build -t ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG} ."
                        echo 'Image has been build'

                        sh "docker push ${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG}"
                        echo 'successfully pushed Image'
                }
            }     
        }
   }    

