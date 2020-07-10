pipeline {
    
    agent any
    
	parameters {
		choice choices: ['awssand01', 'awssand02', 'awssand03'], description: 'Choose from servers', name: 'Server'
	}

	stages {
	
		stage('Initialize') {
		
			environment {
				ENV='.env'
			}
			steps {
				sh 'ELK_VERSION="$(grep ELK_VERSION ${ENV} | awk -F "=" '{print $2}')"'
				sh "echo ${ELK_VERSION}"
				echo "Version: ${ELK_VERSION}"

			}
		}


	}


	post {
		always {
			echo "The overall result is: ${currentBuild.result}"
			echo 'I am always cleaning the Workspace...'
			cleanWs()

		}
		failure {
			echo "It ended with error..."
		}
		success {
			echo "It ended successfully..."
		}
	}
}