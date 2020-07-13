
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
	// agent any
	 agent {
        docker { image 'node:13.8' }
    }
	stages {
		stage("Build"){
			steps {
				sh 'node --version'
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
