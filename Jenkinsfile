pipeline {
    agent any    
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
	    sh "docker stop pik || true"
	    sh "docker run -d --name=pik --rm -p 8888:8080 pik"
	}
    }
};
