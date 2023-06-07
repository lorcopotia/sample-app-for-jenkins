pipeline {
    agent any

    environment {
        GLOBAL_LANG = "ES"
    }

    stages {
         stage('Example Username/Password 1') {
            environment {
                SERVICE_CREDS = credentials('dockerhub-credentials')
            }
            steps {
                sh 'echo "Service user is $SERVICE_CREDS_USR"'
                sh 'echo "Service password is $SERVICE_CREDS_PSW"'
                sh 'docker login -u "$SERVICE_CREDS_USR" -p "$SERVICE_CREDS_PSW"'
            }
        }
        
        stage('Example Username/Password 2') {
            environment {
                SERVICE_CREDS = credentials('jenkins-app-pipeline-credentials-1')
            }
            steps {
                sh 'echo "Service user is $SERVICE_CREDS_USR"'
                sh 'echo "Service password is $SERVICE_CREDS_PSW"'
                
                script {
                    openshift.withCluster() { //openshift.withCluster( 'mycluster' )
                        sh 'oc get pods'
                        
                        try {
                            openshift.withCredentials( 'jenkins-app-pipeline-credentials-1' ) {
                                openshift.newProject( 'borrame-1' )
                                // ...
                                
                            }
                        } catch ( e ) {
                            // The exception is a hudson.AbortException with details
                            // about the failure.
                            "Error encountered: ${e}"
                        }
                    }
                }
            }
        }
    }
}

