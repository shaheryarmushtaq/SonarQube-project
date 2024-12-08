pipeline {
    agent any
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
                // Inject SonarQube token and run analysis
                withCredentials([string(credentialsId: 'sonar-token-id', variable: 'SONARQUBE_TOKEN')]) {
                    withSonarQubeEnv('SonarQube') {
                        // Execute SonarQube analysis
                        sh '''
                            mvn sonar:sonar \
                            -Dsonar.projectKey=my-simple-app \
                            -Dsonar.host.url=http://38.45.71.12:9000 \
                            -Dsonar.login=$SONARQUBE_TOKEN
                        '''
                    }
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
