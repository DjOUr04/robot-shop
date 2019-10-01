pipeline {
    agent any

    environment {
      VARIABLE = credentials('aws_access_key')
    }

    stages {
        stage('init') {
            steps {
              sh
              echo "MSG: ${VARIABLE} "
              sh "kubectl cluster-info"
            }
        }
    }
}
