pipeline {
    agent any

    // Set the Docker Host Environment Variable
    environment {
        DOCKER_HOST = 'tcp://host.docker.internal:2375'  // This tells Jenkins to communicate with Docker Desktop on Windows
	DOCKER_TLS_VERIFY = '0'  // Disable TLS verification (force HTTP)
    }

    stages {
        stage('Verify Docker Connection') {
            steps {
                // Perform a CURL command to verify connectivity to Docker daemon
                sh '''
                    echo "Checking Docker Daemon connectivity..."
                    curl http://host.docker.internal:2375/version
                '''
            }
        }

        stage('Check Docker Version') {
            steps {
                // Check Docker version from Jenkins (should now connect to Docker Desktop on Windows)
                sh 'docker version'
            }
        }

        // Add more stages here as needed for your build
    }
}
