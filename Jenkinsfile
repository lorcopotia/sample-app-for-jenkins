pipeline {
    agent any

    environment {
        GLOBAL_LANG = "ES"
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
    }
}

