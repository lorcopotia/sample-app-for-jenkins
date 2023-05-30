pipeline {
  agent any
  options {
    timeout(time: 20, unit: 'MINUTES') 
  }

    stages {
        stage('Build') {
            steps {
                echo "USER is ${USER}"
                echo "PASS_LC is ${PASS_PROD_LC}"
                echo "PASS_LC is ${PASS_PROD_CN}"
                sh 'printenv'
            }
        }
    }
}
