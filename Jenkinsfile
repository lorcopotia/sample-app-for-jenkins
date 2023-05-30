/* def USER_ = ${USER}
def PASS_PROD_LC_ = ${PASS_PROD_LC} */
pipeline {
  agent any
    environment {
        /* EXAMPLE_CREDS = credentials('example-credentials-id') */
        USER_ = ${USER}
    }
    stages {
        stage('Example') {
            steps {
                /* CORRECT */
                /* sh('curl -u $EXAMPLE_CREDS_USR:$EXAMPLE_CREDS_PSW https://example.com/') */
                echo "USER is ${USER_}"
            }
        }
    }
    stages {
        stage('Build') {
            steps {
                echo "USER is ${USER_}"
                echo "PASS_LC is ${PASS_PROD_LC_}"
                echo "PASS_CN is ${PASS_PROD_CN}"
                sh 'printenv'
            }
        }
    }
}
