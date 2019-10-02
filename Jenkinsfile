pipeline {
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
  serviceAccountName: cd-jenkins
  containers:
  - name: golang
    image: golang:1.10
    command:
    - cat
    tty: true
  - name: gcloud
    image: gcr.io/cloud-builders/gcloud
    command:
    - cat
    tty: true
  - name: kubectl
    image: gcr.io/cloud-builders/kubectl
    command:
    - cat
    tty: true
  """
}
  }

    environment {
      AWS_ACCESS_KEY_ID = credentials('aws_access_key')
      AWS_SECRET_ACCESS_KEY = credentials('aws_secret_key')
      AWS_PROFILE = "eks"
      AWS_DEFAULT_PROFILE = "eks"
      KUBECONFIG = credentials('eks-conf')
    }

    stages {
      stage('kubeconfiguration') {
        steps {
            container('kubectl') {
               sh("kubectl get nodes")
            }
          }
        }
    }
}
