pipeline {
	agent any
	dependencyCheck additionalArguments: '', odcInstallation: 'dependency-check 7.3.0'
	stages {
		stage('Checkout SCM') {
			steps {
				git 'https://github.com/rainyraina/JenkinsDependencyCheck'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
