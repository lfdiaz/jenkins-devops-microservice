
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
	//  agent {
    //     docker { image 'node:13.8' }
    // }
	environment {
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage("Build"){
			steps {
				sh 'docker version'
				sh 'maven --version'
				echo "Build"
				echo "$PATH"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB NAME - $env.JOB_NAME"
				echo "BRANCH - $env.BRANCH_NAME"


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
