pipeline{

       agent any
       environment {
            DOCKERHUB_CREDENTIALS= 'docker-hub'
            IMAGE_NAME='pyflaskapp'
            IMAGE_TAG = 'v3'
       }
  stages {
          stage('Docker login & Build the Image') {
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
                }
            }     
        }
   }    
        stage('docker Push it to docker hub') {
            steps {
                script {
                        sh "docker push index.docker.io/${DOCKERHUB_USERNAME}/${IMAGE_NAME}:${IMAGE_TAG}"
                        echo 'successfully pushed Image'
                        }        
                  }
              }    
         }   
    } 
