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
				bat 'mvn deploy -DmuleDeploy'
			}
		}
	}
}