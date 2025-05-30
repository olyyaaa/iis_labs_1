pipeline {
    agent any

    tools {
        nodejs "NodeJS"
    }

    environment {
        SONARQUBE = 'SonarQube'
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('SonarQube analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarQube Scanner'
                    withSonarQubeEnv(SONARQUBE) {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build step - додай свої команди тут"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}

