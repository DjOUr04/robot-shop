pipeline {
    agent any

    environment {
      USER = credentials('aws_access_key')
      KEY = credentials('aws_secret_key')

    }

    stages {
        stage('init') {
            steps {
              sh
              echo "MSG: ${VARIABLE} "
              sh "kubectl cluster-info"
            }
        }
        stage('kube config'){
          steps {
            withKubeConfig([credentialsId: 'eks-conf', serverUrl: 'https://E47BD1447D64530403105C1F02C1139C.sk1.us-east-2.eks.amazonaws.com']) {
              steps {
                sh 'kubectl get nodes'
              }
            }
          }
        }
    }
}
