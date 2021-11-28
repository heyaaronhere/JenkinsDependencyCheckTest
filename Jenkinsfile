pipeline {
    agent any
    stages {
        stage('Checkout Scm') {
            steps {
                git 'https://github.com/heyaaronhere/JenkinsDependencyCheckTest.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }    
        stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'Default'
			}
		}
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}

}
