pipeline {
    agent any

    environment {
        USER = ""
        PASS_PROD_LC = ""
        PASS_PROD_CN = ""
        
         
    }

    stages {
         stage('Example Username/Password') {
            environment {
                SERVICE_CREDS = credentials('jenkins-app-pipeline-credentials')
            }
            steps {
                sh 'echo "Service user is $SERVICE_CREDS_USR"'
                sh 'echo "Service password is $SERVICE_CREDS_PSW"'
                // sh 'curl -u $SERVICE_CREDS https://myservice.example.com'
            }
        }
        


        stage('Use BuildConfig Variable') {
            steps {
                echo "The variable value is: ${USER}"
                echo "The variable value is: ${PASS_PROD_LC}"
                echo "The variable value is: ${PASS_PROD_CN}"
            }
        }
    }
}

