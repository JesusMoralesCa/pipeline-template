@Library('java-node') _

pipeline {
    agent {
        label('master')
    }

    tools {
        maven 'maven'
    }

    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')
    }

    stages {


/*
        stage('Read properties and checkout') {
            steps {
                WBuild()
                  
                
                
            }
        }
     */
         stage('SonarQube Analysis') {
            steps {
                script{
                  
                    //def sonarProps = readProperties file: 'sonar-project.properties'
                    //def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv('sonarqube') {
                         WBuild()
                        //sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${sonarProps['sonar.projectKey']} -Dsonar.sources=${sonarProps['sonar.sources']}"
                    }                  
                }
            }
        }
    }
}
