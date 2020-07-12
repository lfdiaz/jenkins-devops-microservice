
// Scripted Approach 
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage("Integration Test"){
// 		echo "Integration"
// 	}
// }

// Declarative pipeline
pipeline{
	agent any
	stages {
		stage("Build"){
			steps {
				echo "Build"
			}
		}
		stage("Test"){
			steps {
				echo "Test"
			}
		}
		stage("Integration Test"){
			steps {
				echo "Integration test"
			}
		}
	} 
	post {
		always {
			echo "Im awesome!!!"
		}
		success {
			echo "SUCCESS!!!"
		}
		failure {
			echo "Something went wrong"
		}
	}
}
