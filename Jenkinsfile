pipeline {
    agent any

    environment {
        USER = ""
        PASS_PROD_LC = ""
        PASS_PROD_CN = ""
    }

    stages {
        /* stage('Read BuildConfig') {
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
        } */
        
        stage('Read synced credentials') {
            steps {
                script {
                    openshift.withCluster() {
                        openshift.withProject(env.DEV_PROJECT) {
                            withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: "${env.DEV_PROJECT}-pipeline-credentials", passwordVariable: 'PASS_PROD_LC']]) {
                              // available as an env variable, but will be masked if you try to print it out any which way
                              // note: single quotes prevent Groovy interpolation; expansion is by Bourne Shell, which is what you want
                              sh 'echo $PASS_PROD_LC'
                              // also available as a Groovy variable
                              echo PASS_PROD_LC
                              // or inside double quotes for string interpolation
                              echo "token is $PASS_PROD_LC"
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

