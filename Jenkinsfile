pipeline {
    agent {
        label 'swarn'
    }

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Select environment'
        )
    }

    stages {

        stage('Build') {
            steps {
                echo 'Build started'
            }
        }

        stage('Deploy to PROD') {

            when {
                expression {
                    params.ENVIRONMENT == 'PROD'
                }
            }

            steps {
                echo 'Deploying to PROD'
            }
        }
    }
}
