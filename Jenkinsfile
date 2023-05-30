/* def USER_ = ${USER}
def PASS_PROD_LC_ = ${PASS_PROD_LC} */
pipeline {
  agent any
    environment {
        /* EXAMPLE_CREDS = credentials('example-credentials-id') */
        USER_ = "PEPE${USER}"
    }
    stages {
        stage('Example') {
            steps {
                /* CORRECT */
                /* sh('curl -u $EXAMPLE_CREDS_USR:$EXAMPLE_CREDS_PSW https://example.com/') */
                echo "USER is ${USER_}"
                echo "MSG is ${TEST}"
            }
        }
        stage('Build') {
            steps {
                script {
                    // Obtener el secreto desde OpenShift
			/*
                    def secret = openshift.withCluster() {
                        openshift.withProject('jenkins-app') {
                            openshift.withCredentials([openshiftServiceAccount(credentialsId: 'id-del-secreto')]) {
                                openshift.selector('secret', 'pipeline-credentials').object()
                            }
                        }
                    } */
				}
			}
		}
        
    }
}
