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


        stage('Read properties and checkout') {
            steps {
                WBuild()
                  
                
                
            }
        }
         stage('SonarQube Analysis') {
            steps {
                script{
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv() {
                         
                         checkout scmGit(
                            branches: [[name: '*/main']],
                            extensions: [],
                            userRemoteConfigs: [[url: "https://github.com/JesusMoralesCa/Java-Node.git"]]
                        )
                         def sonarProps = readProperties file: 'sonar-project.properties'
                         sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${sonarProps['sonar.projectKey']} -Dsonar.sources=${sonarProps['sonar.sources']} -Dsonar.language=${sonarProps['sonar.language']} -Dsonar.java.binaries=build/classes"
                        waitForQualityGate abortPipeline: false, credentialsId: credentialsId
                    }                  
                }
            }
        }
    }
}
