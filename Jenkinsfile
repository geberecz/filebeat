

pipeline {
    
    agent any
    
	parameters {
		choice choices: ['awssand01', 'awssand02', 'awssand03'], description: 'Choose from servers', name: 'Server'
	}

	stages {
	
		stage('Create filebeat image in TEST') {
		
			environment {
				DIRECTORY = "test"
			}
			steps {
				// sh 'ELK_VERSION=$(cat test/parameters | grep ELK_VERSION | awk -F "=" '{print $2}')'
				sh 'ELK_VERSION="$(cat test/parameters | grep ELK_VERSION | awk '{print $1}')"'
				sh 'echo "ELK version: ${ELK_VERSION}"'
			}
		}


	}

	/*
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
	*/

}