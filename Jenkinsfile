@Library('java-node') _
import org.foo.*

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
                script {
                    def file = readProperties file: 'project.properties'
                    env.image = file['imageName']
                    WBuild()
                    
                }
            }
        }
    }
}
