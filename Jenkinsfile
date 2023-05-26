@Library('java-node') _


pipeline {
    agent {
        label('master')
    }
    
    
      tools {
        maven 'maven'
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
          withSonarQubeEnv('SonarScanner') {
            sh "sonar-scanner -Dsonar.projectKey=${sonarProps.getProperty('sonar.projectKey')} -Dsonar.sources=${sonarProps.getProperty('sonar.sources')}"
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
