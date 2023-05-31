pipeline {
    agent any

    environment {
        USER = ""
        PASS_PROD_LC = ""
        PASS_PROD_CN = ""
        
        YOUR_CRED = credentials('jenkins-app-pipeline-credentials') 
    }

    stages {
         stage('Read BuildConfig') {
            steps {
                sh 'printenv'
                sh 'echo $YOUR_CRED'

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

