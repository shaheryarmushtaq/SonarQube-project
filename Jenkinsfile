pipeline {
    agent any
    environment {
        SONARQUBE_TOKEN = credentials('Jenkins-Sonar') // Use the token stored as Jenkins-Sonar
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                git 'https://github.com/shaheryarmushtaq/SonarQube-project.git'
            }
        }
        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn clean install'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Run SonarQube analysis
                withSonarQubeEnv('SonarQube') { // Replace 'SonarQube' with the name of the SonarQube server in Jenkins configuration
                    sh '''
                    mvn sonar:sonar \
                        -Dsonar.projectKey=my-simple-app \
                        -Dsonar.host.url=http://38.45.71.12:9000 \
                        -Dsonar.login=$SONARQUBE_TOKEN
                    '''
                }
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }
    }
}
