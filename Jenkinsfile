pipeline {
	agent any
	environment {
		PATH = "/opt/maven/bin:$PATH"
	}

	stages {
		
		stage("build") {
			steps {
				sh 'mvn clean deploy'
			}
		}

		stage("SonarQube Analysis") {
			environment {
				scannerHome = tool 'SonarScanner'
			}

			steps {
				withSonarQubeEnv('SonarServer') {
					sh "${scannerHome}/bin/sonar-scanner"
				}
			}
		}
	}
}
