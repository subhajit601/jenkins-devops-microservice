pipeline {
    agent any

    environment {
        DOCKER_HOST = 'tcp://host.docker.internal:2375'  // Communicate with Docker daemon
        DOCKER_TLS_VERIFY = '0'  // Disable TLS
    }

    stages {
        stage('Setup Docker Context') {
            steps {
                // Create a new Docker context that uses HTTP without TLS
                sh '''
                    echo "Setting up Docker context for HTTP connection..."
                    docker context create host-docker --docker "host=tcp://host.docker.internal:2375"
                    docker context use host-docker
                '''
            }
        }

        stage('Verify Docker Connection') {
            steps {
                // Test the Docker connection using the created context
                sh '''
                    echo "Checking Docker Daemon connectivity..."
                    curl http://host.docker.internal:2375/version
                '''
            }
        }

        stage('Check Docker Version') {
            steps {
                // Use the new context to check Docker version
                sh '''
                    echo "Checking Docker Version..."
                    docker --context host-docker version
                '''
            }
        }
    }
}
