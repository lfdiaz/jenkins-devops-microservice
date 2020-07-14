
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
		stage("Checkout"){
			steps {
				sh 'docker version'
				sh 'mvn --version'
				echo "Build"
				echo "$PATH"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD ID - $env.BUILD_ID"
				echo "JOB NAME - $env.JOB_NAME"
				echo "BRANCH - $env.BRANCH_NAME"


			}
		}
		stage("Compile"){
			steps {
				sh "mvn clean compile"
			}
		}
		stage("Test"){
			steps {
				sh "mvn test"
			}
		}
		stage("Integration Test"){
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage("Package"){
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage("Build Docker image"){
			steps {
				// sh "docker build -t luisdiazc2/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("luisdiazc2/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}

		stage("Push Docker image"){
			steps {
				script {
					docker.withRegistry("", 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
