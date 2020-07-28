
pipeline {
    
    agent any
    
	parameters {
		choice choices: ['Create new image for filebeat', 'Deploy filebeat to server'], description: 'Do you want to create new image, or deploy existing one?', name: 'ACTION'
		choice choices: ['awssand01', 'awssand02', 'awssand03'], description: 'If you want to deploy, choose destination from list.', name: 'SERVER'
	}

	stages {
	
		stage('Create filebeat image in TEST') {
			
			when { expression { BRANCH_NAME == "develop" && params.ACTION == "Create new image for filebeat" }}
		
			environment {
				DIRECTORY = "test"
			}
			
			steps {
				sh 'ELK_VERSION=$(grep ELK_VERSION ${DIRECTORY}/parameters | awk -F "=" {\'print $2\'}) && \
				    sed -i -E "s/(filebeat-oss:+)(.*)/filebeat-oss:${ELK_VERSION}/g" ${DIRECTORY}/filebeat-context/Dockerfile'

				/* It is runable only in the Kuoni site
				script {
					docker.withRegistry('https://kuonitumlare-docker.jfrog.io', 'artifactory-credentials') {
						def image = docker.build("filebeat-${DIRECTORY}:${env.BUILD_ID}", "./${DIRECTORY}/filebeat-context")
						image.push()
						image.push('latest')
					}
				}
				*/
			}
		}


	}

	/*
	post {
		always {
			echo "The overall result is: ${currentBuild.result}"
			echo "I am always cleaning the Workspace..."
			cleanWs()

		}
		failure {
			echo "It ended with error..."
		}
		success {
			echo "It ended successfully..."
		}
	}
	*/

}