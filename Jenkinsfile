//DECLARATIVE PIPELINE
pipeline {
	// agent { docker { image 'maven:3.6.3'}}
	agent { docker { image 'node:20.9'}}
	stages {
		stage ('Build') {
			steps {
				//sh 'mv --version'
				sh 'node --version'
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
