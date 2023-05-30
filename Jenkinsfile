pipeline {
    agent any

    environment {
        MY_VAR = ""
    }

    stages {
        stage('Read BuildConfig') {
            steps {
                script {
                    openshift.withCluster() {
                        openshift.withProject(env.DEV_PROJECT) {
                            openshift.withEnv('my-buildconfig') { envVars ->
                                // Accede a las variables de entorno del BuildConfig
                                MY_VAR = envVars.MY_VARIABLE
                            }
                        }
                    }
                }
            }
        }

        stage('Use BuildConfig Variable') {
            steps {
                echo "The variable value is: ${MY_VAR}"
            }
        }
    }
}

