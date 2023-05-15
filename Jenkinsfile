@Library('java-node') _


pipeline {
    agent {
        label('master')
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
