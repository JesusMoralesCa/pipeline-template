@Library('java-node') _


pipeline {
    agent {
        label('master')
    }
    
    
      tools {
        maven 'maven'
        sonarRunner 'SonarScanner'
    }

    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')

    }
    
   stages {
        stage('SCM') {
      steps {
        checkout scm
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script {
          def sonarProps = readProperties file: 'sonar-project.properties'
          withSonarQubeEnv('sonarqube') {
              sh "sonar-scanner -Dsonar.projectKey=${sonarProps['sonar.projectKey']} -Dsonar.sources=${sonarProps['sonar.sources']}"
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
