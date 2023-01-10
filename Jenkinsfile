pipeline {
		// agent any
		agent { docker { image 'node:3.16'} }
		stages {
			stage('Build') {
				steps {
					sh 'node --version'
					echo "Build"
				}
			}
			stage('Test') {
				steps {
					echo "Test"
	
				}
			}
			stage('Integration Test') {
				steps {
					echo "IntegrationTest"
	
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
