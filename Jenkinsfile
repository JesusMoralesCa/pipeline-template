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
        stage('SCM') {
            steps {
                checkout scm
                script{
                        checkout scmGit(
                            branches: [[name: '*/main']],
                            extensions: [],
                            userRemoteConfigs: [[url: 'https://github.com/JesusMoralesCa/Java-Node.git']]
                        )
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    def sonarProps = readProperties file: 'sonar-project.properties'
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv {
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=${sonarProps['sonar.projectKey']}"
                    }
                }
            }
        }

        stage('Read properties and checkout') {
            steps {
                WBuild()
            }
        }
    }
}
