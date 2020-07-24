pipeline {
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				bat 'mvn clean package'
			}
		stage('Deploy') {
			steps {
				sh 'Deploying App to Cloudhub'
				bat 'mvn deploy -DmuleDeploy'
			}
		}
	}
}