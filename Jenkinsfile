pipeline {
		agent any

		environment {
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		
		stages {
			stage('Checkout') {
				steps {
					// sh 'node --version'
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "PATH - $PATH"
					echo "BUILD_NUMBER - $env.BUILD_NUMBER"
					echo "BUILD_ID - $env.BUILD_ID"
					echo "JOB_NAME - $env.JOB_NAME"
					echo "BUILD_TAG - $env.BUILD_TAG"
					echo "BUILD_URL - $env.BUILD_URL"
				}
			}
			stage('Compile') {
				steps {
					sh "mv clean compile"
				}
			}
			stage('Test') {
				steps {
					sh "mvn test"	
				}
			}
			stage('Integration Test') {
				steps {
					sh 'mvn failsafe:integration-test failsafe:verify'
				}
			}

			stage('Package') {
				steps {
					sh 'mvn package -DskipTests'
				}
			}
			stage('Build Docker Image') {
				steps {
					script {
						dockerImage = docker.build("docker build -t giannisdock/javaimage:${env.BUILD_TAG}")

					}
				}
			}
			stage('Push Docker Image') {
				steps {
					dockerImage.withRegistry('', 'dockerHub') {
						dockerImage.push();
						dockerImage.push('latest');

					}
				}
			}

		} 
		post {
			always {
				echo "Run always"
			}
			success {
				echo "when is running succesfully"
			}
			failure {
				echo "when is failing"
			}
			changed {
				echo "something has changed"
			}
		}

}
