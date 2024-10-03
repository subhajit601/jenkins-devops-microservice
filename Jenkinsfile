//DECLARATIVE PIPELINE
pipeline {
	agent { docker { image 'maven:3.6.3'}}
	stages {
		stage ('Build') {
			steps {
				sh 'mv --version'
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
