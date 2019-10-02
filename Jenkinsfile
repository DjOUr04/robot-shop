node {
  label 'master'

  stage('List pods') {
    withKubeConfig([clusterName: 'dou.us-east-2.eksctl.io', namespace: 'dio',credentialsId: 'eks-conf', serverUrl: 'https://E47BD1447D64530403105C1F02C1139C.sk1.us-east-2.eks.amazonaws.com']) {
      sh 'kubectl get pods'
    }
  }
}
