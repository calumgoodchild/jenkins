pipeline {
	agent none


	/*options {
		checkoutToSubdirectory("/var/www/")
	}*/

	stages {

		stage('Pre-Build') {
			agent any
			steps {
				sh '''
					printenv
					ls -la /var/
					echo $(date)

				'''
			}
		}

		stage("Build") {
			agent any
			steps {
				echo "Building...${env.BUILD_ID}" 
			}
		}

		stage("Build on Ubuntu") {
			/*agent {
				docker {
					image 'ubuntu:latest'
					args '-v /var/run/docker.sock:/var/run/docker.sock'
				}
			}*/
			agent any
			steps {
				sh '''
					echo "THIS IS FROM A UBUNTU DOCKER CONTAINER"
					printenv
				'''
			}
		}

		stage("Test") {
			agent any
			steps {
				echo "Testing...${env.BUILD_ID}"
			}
		}

		stage("Deploy") {
			agent any
			steps {
				echo "Deploying...${env.BUILD_ID}" 
				sh 'echo "BUILD ON PUSH FROM GIT"'
			}
		}

	}

	post {
        failure {
            echo 'Sending email...'
            
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
		                recipientProviders: [
		                	[$class: 'DevelopersRecipientProvider'], 
		                	[$class: 'RequesterRecipientProvider']
		                ],
		                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
        }
    }
}