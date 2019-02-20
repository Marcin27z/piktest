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
    post {
    	always {
            archiveArtifacts artifacts: 'target/*.war', fingerprint: true
	    sh "docker build -t pik ."
	    sh "docker run -it --rm -p 8888:8081 pik"
	}
    }
};
