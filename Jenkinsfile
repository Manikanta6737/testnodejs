pipeline {

  environment {
    PROJECT = "still-smithy-279711"
    APP_NAME = "node"
    FE_SVC_NAME = "${APP_NAME}"
    CLUSTER = "sample"
    CLUSTER_ZONE = "us-central1-c"
    IMAGE_TAG = "us.gcr.io/${PROJECT}/${APP_NAME}:latest"
    JENKINS_CRED = "${PROJECT}"
  
  }

  agent {
    kubernetes {
      label 'nodejs'
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
  - name: node
    image: us.gcr.io/still-smithy-279711/nodejs
    command:
    - cat
    tty: true
  - name: helm
    image: us.gcr.io/still-smithy-279711/helm3
    command:
    - cat
    tty: true
  
"""
}
  }
  tools {nodejs "nodejs"}
    stages {    
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }      
  }   
} 
