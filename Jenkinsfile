pipeline {
    agent any

    environment {
        // Set Docker Host to communicate with the Docker daemon without TLS
        DOCKER_HOST = 'tcp://host.docker.internal:2375'
        DOCKER_TLS_VERIFY = '0'  // Disable TLS verification
        DOCKER_API_VERSION = '1.41' // You may also want to set this for compatibility (optional)
    }

    stages {
        stage('Verify Docker Connection') {
            steps {
                // Use curl to check Docker daemon connection
                sh '''
                    echo "Checking Docker Daemon connectivity..."
                    curl http://host.docker.internal:2375/version
                '''
            }
        }

        stage('Check Docker Version') {
            steps {
                // Add environment variable to force HTTP usage for Docker commands
                sh '''
                    echo "Checking Docker Version..."
                    export DOCKER_HOST=tcp://host.docker.internal:2375
                    export DOCKER_TLS_VERIFY=0
                    docker --debug version
                '''
            }
        }
    }
}
