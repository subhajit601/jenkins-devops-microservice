//DECLARATIVE PIPELINE
pipeline {
	// agent { docker { image 'maven:3.6.3'}}
	//agent { docker { image 'node:20.9'}}
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		 // Set Docker Host to communicate with the Docker daemon without TLS
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
		stage('Test Docker') {
            steps {
                //sh 'echo $DOCKER_HOST'
                // Use the new context to check Docker version
                sh '''
                    echo "Checking Docker Version..."
                    docker --context host-docker version
                '''
            }
        }
		stage ('Build') {
			steps {
				sh 'mv --version'
				sh '''
                    echo "Checking Docker Version..."
                    docker --context host-docker version
                '''
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage ('Test') {
			steps {
				echo "Test"
			}
		}
		stage ('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo 'I will always run...'
		}
		success {
			echo 'I will when build is success'
		}
		failure {
			echo 'I will when build is failed'
		}
		changed {
			echo 'I will when build is changed'
		}
	}
}
