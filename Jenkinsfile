pipeline {
    agent any

    tools {
        sonarRunner 'SonarScanner'
    }

    environment {
        DOCKER_HUB_REPO = 'kamatagi89/ecommerce-app'
    }

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        sonar-scanner \
                        -Dsonar.projectKey=ecommerce-app \
                        -Dsonar.projectName="E-Commerce Application" \
                        -Dsonar.sources=server,public
                    '''
                }
            }
        }
    }
}
