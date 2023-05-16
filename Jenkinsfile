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
        stage('Read properties and checkout') {
            steps {
                    hola()
                    WBuild()

            }
        }
    }
}
