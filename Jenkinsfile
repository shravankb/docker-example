pipeline {
    agent any

    stages {
        stage('Basic Setup') {
            steps {
                echo 'Basic Setup and checks'
                sh 'node --version'
                sh 'npm --version'
                
                echo 'Install Project Dependencies'
                sh 'npm i'

            }
        }
        stage('Unit Testing') {
            steps {

                echo 'UMS Testing-in-Progress'
                sh 'npm run coverage'
            
            }
        }

        stage('SonarQube Scanner Analysis') {
            environment {
                scannerHome = tool 'sonar_scanner'
            }
            
            steps{
                echo 'Check Testing'

                withSonarQubeEnv('SonarQube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                

            }
        }

        stage('Build'){

            steps{
                echo "Building Image"
            }

        }
    }
}