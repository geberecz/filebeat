

pipeline {
    
    agent any
    
	parameters {
		choice choices: ['Create new image for filebeat', 'Deploy filebeat to server'], description: 'What do you want to do?', name: 'ACTION'
		string defaultValue: '7.7.0', description: 'Some text...', name: 'ELK_VERSION', trim: false
		choice choices: ['awssand01', 'awssand02', 'awssand03'], description: 'Choose from servers', name: 'SERVER'
	}

	stages {
	
		stage('Create filebeat image in TEST') {
			
			when { expression { BRANCH_NAME == "develop" && params.ACTION == "Create new image for filebeat" }}
		
			environment {

				DIRECTORY = "test"
			}
			
			steps {
				
				sh 'sed -i -E "s/(ARG+)([0-9].*)/\1 $ELK_VERSION/g" test/filebeat-context/Dockerfile'
	            sh 'cat test/filebeat-context/Dockerfile'
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