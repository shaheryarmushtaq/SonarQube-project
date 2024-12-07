pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-credentials', url: 'https://github.com/shaheryarmushtaq/SonarQube-project.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube Analysis...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }
}
