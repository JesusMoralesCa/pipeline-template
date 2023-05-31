@Library('SharedLibraryTest') _

pipeline {
    agent {
        label('master')
    }

    tools {
        maven 'maven'
        nodejs 'Node'
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
    }
}
