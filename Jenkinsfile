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
				script {
					def proceed = true
                    try {
						timeout(time: 100, unit: 'SECONDS') {
							input('Continue to Deploy?')
        	    	    } catch (err) {
                        proceed = false
                    }
                    if(proceed) {
                    	bat 'mvn deploy -DmuleDeploy'
					}
				}
			}
		}
	}
}