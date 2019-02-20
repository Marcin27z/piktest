pipeline {
    agent {
        docker {
            image 'openjdk:8-jre-alpine'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
		def mvnHome = tool 'M3'
                sh '${mvnHome}/bin/mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
};
