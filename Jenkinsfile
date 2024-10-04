//DECLARATIVE PIPELINE
pipeline {
	// agent { docker { image 'maven:3.6.3'}}
	//agent { docker { image 'node:20.9'}}
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		DOCKER_HOST = "tcp://localhost:2375"
        DOCKER_TLS_VERIFY = ""

	}
	stages {
		stage ('Build') {
			steps {
				sh 'mv --version'
				sh 'echo $DOCKER_HOST'
				sh 'docker -H tcp://localhost:2375 version'
				//sh 'docker version'
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
