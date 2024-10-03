//DECLARATIVE PIPELINE
pipeline {
	agent any
	stages {
		stage ('Build') {
			steps {
				echo "Build"
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
	} post {
		always {
			echo 'I will always run...'
		}
		success {
			echo 'I will when build is success'
		}
		failure {
			echo 'I will when build is failed'
		}
	}
}
