pipeline {

  environment {
    PROJECT = "still-smithy-279711"
    APP_NAME = "gceme"
    FE_SVC_NAME = "${APP_NAME}-frontend"
    CLUSTER = "jenkins"
    CLUSTER_ZONE = "us-central1-c"
    IMAGE_TAG = "us.gcr.io/${PROJECT}/${APP_NAME}:latest"
    JENKINS_CRED = "${PROJECT}"
  }

  agent {
    kubernetes {
      label 'sample-app'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
labels:
  component: ci
spec:
  # Use service account that can deploy to all namespaces
  
  containers:
  - name: gcloud
    image: us.gcr.io/still-smithy-279711/gcloud
    command:
    - cat
    tty: true
  
"""
}
  }
  stages { 
    stage('Docker Build') {
       steps {
           sh 'docker build -t nodeimage:v1 .'
      }
    }
  }
}  
  
