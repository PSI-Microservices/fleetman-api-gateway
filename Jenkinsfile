pipeline {
   agent any

   environment {
     // You must set the following environment variables
       ORGANIZATION_NAME       = "PSI-Microservices"
       YOUR_DOCKERHUB_USERNAME = "tatacyprian"

     SERVICE_NAME = "fleetman-api-gateway"
     REPOSITORY_TAG="${YOUR_DOCKERHUB_USERNAME}/${ORGANIZATION_NAME}-${SERVICE_NAME}:${BUILD_ID}"
   }

   stages {
      stage('Preparation') {
         steps {
            cleanWs()
            git credentialsId: 'GitHub', url: "https://github.com/${ORGANIZATION_NAME}/${SERVICE_NAME}"
         }
      }
      stage('Build') {
         steps {
            sh '''mvn clean package'''
         }
      }

      //stage('Build and Push Image') {
      //   steps {
       //    sh 'docker image build -t ${REPOSITORY_TAG} .'
       //  }
     // }

      }
   }
}
