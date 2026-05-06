pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/pharoth9999/springboot-jenkins-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
}