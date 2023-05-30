pipeline {
    agent any

    environment {
        USER = ""
        PASS_PROD_LC = ""
        PASS_PROD_CN = ""
    }

    stages {
        stage('Read BuildConfig') {
            steps {
                script {
                    openshift.withCluster() {
                        openshift.withProject(env.DEV_PROJECT) {
                            openshift.withEnv('new-jenkins-pipeline') { //envVars ->
                                // Accede a las variables de entorno del BuildConfig
                                USER = envVars.USER
                                PASS_PROD_LC = envVars.PASS_PROD_LC
                                PASS_PROD_CN = envVars.PASS_PROD_CN
                            }
                        }
                    }
                }
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

