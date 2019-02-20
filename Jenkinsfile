pipeline {
    agent {
        docker {
            image 'openjdk:8-jre-alpine'
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
	def mvnHome
	stage('Preparation') {
	    mvnHome = tool 'M3'
	}
        stage('Build') {
	    steps {
                sh "'${mvnHome}/bin/mvn' clean install"
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
};
