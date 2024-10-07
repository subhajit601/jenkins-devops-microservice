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
                // Set up Docker context for HTTP communication without TLS
                sh '''
                    echo "Setting up Docker context for HTTP connection..."
                    docker context create host-docker --docker "host=tcp://host.docker.internal:2375"
                    docker context use host-docker
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mv --version'  // Check if mv is installed and version
                sh 'docker --context host-docker version'  // Check Docker version using custom context
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
            echo 'I will run when build is successful'
        }
        failure {
            echo 'I will run when the build fails'
        }
        changed {
            echo 'I will run when the build result changes'
        }
    }
}
