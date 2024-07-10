pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('8c7552b9-e48a-44ca-ab3b-98d38d1bcc60')
    }
    stages {
        stage('Install npm dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Run security tests') {
            steps {
                bat 'npm audit'
            }
        }
        stage('Run integration tests') {
            steps {
                bat 'npm test'
            }
        }
        stage('Sample stage') {
            steps {
                echo "%DOCKERHUB_CREDENTIALS_USR%"
            }
        }
        stage('Build Docker image') {
            steps {
                bat 'docker build -t hris96/student-registry-app-jenkinsfile:%BUILD_NUMBER% .'
            }
        }
        stage('Push image to DockerHub') {
            steps {
                bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
                bat 'docker push hris96/student-registry-app-jenkinsfile:%BUILD_NUMBER%'
                bat 'docker tag hris96/student-registry-app-jenkinsfile:%BUILD_NUMBER% hris96/student-registry-app-jenkinsfile:latest'
                bat 'docker push hris96/student-registry-app-jenkinsfile:latest'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}