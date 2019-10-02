pipeline {
  agent {
    kubernetes {
      label 'sample-app'
      defaultContainer 'jnlp'
      yaml """
  spec:
    containers:
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
            withKubeConfig([credentialsId: 'eks-conf', serverUrl: 'https://E47BD1447D64530403105C1F02C1139C.sk1.us-east-2.eks.amazonaws.com']) {
              steps {
                sh "kubectl get nodes"
              }
            }
          }
        }
    }
}
