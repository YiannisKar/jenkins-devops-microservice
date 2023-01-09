pipeline {
		agent any
		stages {
			stage('Build') {
				steps {
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
		}

}
