pipeline {
    agent any

    environment {
        // Docker and Maven paths
        dockerHome = tool 'myDocker'
        mavenHome = tool 'myMaven'
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"

        // Docker connection settings (using HTTP)
        DOCKER_HOST = 'tcp://host.docker.internal:2375'
        DOCKER_TLS_VERIFY = '0'
    }

    stages {
        stage ('Setup Docker Context') {
            steps {
                // Check if the Docker context already exists, otherwise create it
                sh '''
                    echo "Checking if Docker context 'host-docker' exists..."
                    if docker context inspect host-docker > /dev/null 2>&1; then
                        echo "Docker context 'host-docker' already exists, switching to it..."
                    else
                        echo "Creating Docker context 'host-docker'..."
                        docker context create host-docker --docker "host=tcp://host.docker.internal:2375"
                    fi
                    docker context use host-docker
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mv --version'  // Check mv command
                sh 'docker --context host-docker version'  // Use Docker with the custom context
                echo "Build Stage"
                echo "PATH: $PATH"
                echo "BUILD_NUMBER: $env.BUILD_NUMBER"
                echo "BUILD_ID: $env.BUILD_ID"
                echo "JOB_NAME: $env.JOB_NAME"
                echo "BUILD_TAG: $env.BUILD_TAG"
                echo "BUILD_URL: $env.BUILD_URL"
            }
        }

        stage ('Test') {
            steps {
                echo "Test Stage"
            }
        }

        stage ('Integration Test') {
            steps {
                echo "Integration Test Stage"
            }
        }
    }

    post {
        always {
            echo 'I will always run...'
        }
        success {
            echo 'I will run when bui
