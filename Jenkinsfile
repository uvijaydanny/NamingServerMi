pipeline {
agent any
    tools {
        maven 'localMaven'
    }
stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'
                bat "docker build . -t namingserver:${env.BUILD_ID}"
            }
        }
        
        stage('Run') {
        	steps {
        		bat "docker run -p 8761:8761 -d namingserver:${env.BUILD_ID}"
        	}
        }
    }
}