pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
    }

    post {
    success {
        emailext(
            to: "phathyroth@gmail.com",
            subject: "SUCCESS - Thy Pharoth",
            body: "Build SUCCESS: ${env.BUILD_URL}",
            mimeType: 'text/plain'
        )
    }

    failure {
        emailext(
            to: "phathyroth@gmail.com",
            subject: "FAILED - Thy Pharoth",
            body: "Build FAILED: ${env.BUILD_URL}",
            mimeType: 'text/plain'
        )
    }
}
}
}