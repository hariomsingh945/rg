pipeline {
    agent any

    parameters {
        string(
            name: 'APP_NAME',
            defaultValue: 'myapp',
            description: 'Enter application name'
        )
        booleanParam(
            name: 'DEPLOY',
            defaultValue: false,
            description: 'Do you want to deploy?'
        )
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Select deployment environment'
        )
        password(
            name: 'APP_PASSWORD',
            defaultValue: '',
            description: 'Enter application password'
        )



    }

    stages {
        stage('Parameter-Demo') {
            steps {
                echo "Application Name: ${params.APP_NAME}"
            }
        }
    }
}
