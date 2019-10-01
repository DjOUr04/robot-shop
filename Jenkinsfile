pipeline {
    agent any
    stages {
        stage('Pull Request') {
            steps {
                echo 'A new commit in the features branch has been detected'
                input(message: "Do you want to create a Pull Request?", ok: "yes")
                httpRequest authentication: 'git_user', contentType: 'APPLICATION_JSON_UTF8', httpMode: 'POST', requestBody: """{ "title": "Pull Request Created Automatically by Jenkins", "body": "From Jenkins job: ${env.BUILD_URL}", "head": "mons3rrat:${env.BRANCH_NAME}", "base": "master"}""", url: "https://api.github.com/repos/mons3rrat/robot-shop/pulls"
            }
        }
    }
}
