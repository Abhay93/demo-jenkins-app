pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				bat 'mvn clean package'
			}
		}
		stage('Deploy') {
			steps {
				timeout(time: 100, unit: 'SECONDS') {
					input('Continue to Deploy?')
        	        }
				bat 'mvn deploy -DmuleDeploy'
			}
		}
	}
}