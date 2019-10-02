node {
  label 'master'
  
  stage('List pods') {
    withKubeConfig([credentialsId: 'eks-conf', serverUrl: 'https://E47BD1447D64530403105C1F02C1139C.sk1.us-east-2.eks.amazonaws.com']) {
      sh 'kubectl get pods'
    }
  }
}
