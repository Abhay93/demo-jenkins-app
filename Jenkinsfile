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
					timeout(time: 100, unit: 'SECONDS') {
					input('Continue to Deploy?')
                	bat 'mvn deploy -DmuleDeploy'
					}
				}
			}
		}
	}
	post { 
        always { 
            echo 'Always Condition!'
        } 
        changed { 
            echo 'Changed Condition!'
        } 
        fixed { 
            echo 'Fixed Condition!'
        } 
        regression { 
            echo 'Regression Condition!'
        } 
        aborted { 
            echo 'Aborted Condition!'
        } 
        failure { 
            echo 'Failure Condition!'
        } 
        success { 
            echo 'Success Condition!'
        } 
        unstable { 
            echo 'Unstable Condition!'
        } 
        unsuccessful { 
            echo 'Unsuccessful Condition!'
        } 
        cleanup { 
            echo 'Cleanup Condition!'
        }
        
        
        
    }
}