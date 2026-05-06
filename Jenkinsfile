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
                to: 'your_email@example.com',
                subject: "SUCCESS - springboot-jenkins-project - Thy Pharoth",
                body: "Build SUCCESS ✔\nURL: ${env.BUILD_URL}"
            )
        }

        failure {
            emailext(
                to: 'your_email@example.com',
                subject: "FAILED - springboot-jenkins-project - Thy Pharoth",
                body: "Build FAILED ❌\nCheck: ${env.BUILD_URL}"
            )
        }
    }
}