pipeline {
	agent any

	stages {

		stage('Build') {
			steps {
				echo 'Building...${env.BUILD_ID}' 
			}
		}

		stage('Test') {
			steps {
				echo 'Testing...${env.BUILD_ID}'
			}
		}

		stage('Deploy') {
			steps {
				echo 'Deploying...${env.BUILD_ID}' 
			}
		}

	}
}