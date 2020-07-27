def ELK_VERSION

pipeline {
    
    agent any
    
	parameters {
		choice choices: ['awssand01', 'awssand02', 'awssand03'], description: 'Choose from servers', name: 'Server'
	}

	stages {
	
		stage('Create filebeat image in TEST') {
		
			environment {
				ELK_VERSION = sh 'cat test/parameters'
			}
			steps {
				echo "ELK version is: ${ELK_VERSION}"

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