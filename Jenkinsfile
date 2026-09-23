pipeline {
    agent any

    parameters {

        // 1. String parameter
        string(
            name: 'APP_NAME',
            defaultValue: 'myapp',
            description: 'Enter application name'
        )

        // 2. Boolean parameter
        booleanParam(
            name: 'DEPLOY',
            defaultValue: false,
            description: 'Do you want to deploy?'
        )

        // 3. Choice parameter
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Select deployment environment'
        )

        // 4. Text parameter
        text(
            name: 'RELEASE_NOTES',
            defaultValue: 'Initial release',
            description: 'Enter release notes'
        )

        // 5. Password parameter
        password(
            name: 'DEPLOY_PASSWORD',
            defaultValue: '',
            description: 'Enter deployment password'
        )
    }

    stages {

        stage('Show Parameters') {
            steps {
                echo "================================"
                echo "Application : ${params.APP_NAME}"
                echo "Environment : ${params.ENVIRONMENT}"
                echo "Deploy      : ${params.DEPLOY}"
                echo "Release Notes:"
                echo "${params.RELEASE_NOTES}"
                echo "================================"
                echo "Deployment password received"
            }
        }

        stage('Deployment') {
            steps {
                script {

                    if (params.DEPLOY) {
                        echo "Starting deployment..."
                        echo "Application: ${params.APP_NAME}"
                        echo "Environment: ${params.ENVIRONMENT}"
                        echo "Deployment completed"
                    } else {
                        echo "Deployment skipped"
                    }
                }
            }
        }
    }
}
