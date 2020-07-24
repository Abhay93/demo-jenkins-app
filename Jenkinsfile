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
				input('Continue to Deploy?')
				bat 'mvn deploy -DmuleDeploy'
			}
		}
	}
}