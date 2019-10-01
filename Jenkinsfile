pipeline {
    agent any

    environment {
      VARIABLE = credentials('aws_access_key')
    }

    stages {
        stage('init') {
            steps {
                echo "MSG: ${VARIABLE} is missing!"
                sh "kubectl cluster-info"
            }
        }
    }
}
