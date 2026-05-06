pipeline {
    agent any

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    tools {
        maven 'Maven3'
    }

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                sh 'ansible-playbook -i inventory.ini deploy.yml'
            }
        }
    }

    post {

        success {
            emailext(
                to: "phathyroth@gmail.com",
                subject: "SUCCESS - Thy Pharoth",
                body: """
BUILD SUCCESS

URL:
http://178.128.93.188/Midterm-2026/thy-pharoth

Build Number: ${env.BUILD_NUMBER}
Jenkins URL: ${env.BUILD_URL}
"""
            )
        }

        failure {
            emailext(
                to: "phathyroth@gmail.com",
                subject: "FAILED - Thy Pharoth",
                body: """
BUILD FAILED

Check Jenkins:
${env.BUILD_URL}

Build Number: ${env.BUILD_NUMBER}
"""
            )
        }
    }
}