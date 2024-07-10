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
                echo "${BUILD_NUMBER}"
                echo '${DOCKERHUB_CREDENTIALS_USR}'
            }
        }
    }
}