pipeline {
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
