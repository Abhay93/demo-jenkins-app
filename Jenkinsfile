pipeline {
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				mvn clean package
			}
		stage('Deploy') {
			steps {
				sh 'Deploying App to Cloudhub
				mvn deploy -DmuleDeploy'
			}
		}
	}
}