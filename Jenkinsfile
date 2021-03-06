pipeline {
	agent any
	environment {
        RECIPIENTS_EMAIL = 'muletutorials@gmail.com'
    }
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
        	    	    }
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
	post { 
        always { 
            echo 'Always Condition!'
			archiveArtifacts artifacts: 'demo-pipeline.jar'
            sendEmail(currentBuild.currentResult);
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
def sendEmail(status) {
    mail(
            to: "$EMAIL_RECIPIENTS",
            subject: "Build $BUILD_NUMBER - " + status + " (${currentBuild.fullDisplayName})",
            body: "Check console output at: $BUILD_URL/console" + "\n")
}
