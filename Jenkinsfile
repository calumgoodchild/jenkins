pipeline {
	agent any

	/*options {
		checkoutToSubdirectory("/var/www/")
	}*/

	stages {

		stage('Pre-Build') {
			steps {
				sh '''
					printenv
					mkdir /var/www/html
				'''
			}
		}

		stage("Build") {
			steps {
				echo "Building...${env.BUILD_ID}" 
			}
		}

		stage("Test") {
			steps {
				echo "Testing...${env.BUILD_ID}"
			}
		}

		stage("Deploy") {
			steps {
				echo "Deploying...${env.BUILD_ID}" 
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