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
	stage('Printing environment vars') {
	    steps {
                sh 'printenv'
            }
	}
        }
        stage('Build') {
            steps {
                script {
                            openshift.withCluster() {
                                openshift.withProject(env.DEV_PROJECT) {
                                openshift.newBuild("--name=el-nuevo", "--image-stream=openshift/redhat-openjdk18-openshift:1.8", "--binary")
                                }
                            }
			}
	    }
	}   
    }
}
