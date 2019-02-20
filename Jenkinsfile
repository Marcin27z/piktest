pipeline {
    agent {
        docker {
            image 'maven:latest'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    tools {
    maven 'M3'
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
	    steps {
                sh "mvn clean install"
            }
        }
    }
};
