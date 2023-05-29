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
                    checkout scmGit(
                        branches: [[name: '*/main']],
                        extensions: [],
                        userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/pipeline-template.git']]
                    )
                    WBuild()
                    def sonarProps = readProperties file: 'sonar-project.properties'
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv {
                        
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${sonarProps['sonar.projectKey']} -Dsonar.sources=${sonarProps['sonar.sources']}"
                    }                  
                }
            }
        }
    }
}
