@Library('java-node') _


pipeline {
    agent {
        label('master')
    }
    

    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-jesusmoralesc')
        
    }
    
   stages {
        stage('Read properties and checkout') {
            steps {
                script {
                    def file = readProperties file: 'project.properties'
                    env.image = file['imageName']
                    WBuild()
                    
                }
            }
        }
    }
}
