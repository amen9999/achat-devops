pipeline {
    agent any
    
    tools {
        maven 'maven-3.9.4'
    }
    
    stages {
        
        stage('Checkout GIT') {
            steps {
                echo 'Récupération du code depuis GitHub...'
            }
        }
        
        stage('Maven Build') {
            steps {
                echo 'Compilation Maven...'
                dir('achat/achat') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
        
        stage('Maven Test') {
            steps {
                echo 'Tests unitaires...'
                dir('achat/achat') {
                    sh 'mvn test'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Analyse SonarQube...'
                withSonarQubeEnv('sonarqube') {
                    dir('achat/achat') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }

        stage('Deploy to Nexus') {
            steps {
                echo 'Déploiement vers Nexus...'
                dir('achat/achat') {
                    sh 'mvn deploy -DskipTests'
                }
            }
        }
        
    }
    
    post {
        success {
            echo 'Build réussi !'
        }
        failure {
            echo 'Build échoué !'
        }
    }
}
