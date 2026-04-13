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
