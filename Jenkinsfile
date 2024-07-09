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
    }
}