def USER_ = ${USER}
def PASS_PROD_LC_ = ${PASS_PROD_LC}
pipeline {
  agent any
  options {
    timeout(time: 20, unit: 'MINUTES') 
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
