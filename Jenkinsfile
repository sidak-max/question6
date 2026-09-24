pipeline {
    agent any

    environment {
        APP_NAME = 'Student Management System'
        APP_VERSION = '1.0'
    }

    parameters {
        booleanParam(
            name: 'SEND_EMAIL',
            defaultValue: false,
            description: 'Send notification email'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sidak-max/question6.git'
            }
        }

        stage('Build') {
            steps {
                bat 'python -m py_compile app.py'

                echo "Application: ${APP_NAME}"
                echo "Version: ${APP_VERSION}"
            }
        }

        stage('Send Notification') {
            when {
                expression {
                    params.SEND_EMAIL == true
                }
            }

            steps {
                echo "Email Subject: ${APP_NAME} ${APP_VERSION}"
                echo "Build notification sent"
            }
        }
    }
}
