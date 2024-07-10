pipeline {
    agent any
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
                echo "${USERNAME}"
            }
        }
    }
}