pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'PROD'],
            description: 'Select deployment environment'
        )
    }

    environment {
        AZURE_CREDS = credentials('azure-svc-azure-service-principal')
    }

    stages {

        stage('azure-login') {
            steps {
                sh 'az login --service-principal -u "$AZURE_CREDS_CLIENT_ID" -p "$AZURE_CREDS_CLIENT_SECRET" -t "$AZURE_CREDS_TENANT_ID"'
                sh 'az account set --subscription "$AZURE_CREDS_SUBSCRIPTION_ID"'
                sh 'az account show'
            }
        }

        stage('terraform init') {
            steps {
                sh 'terraform init'
                sh 'terraform fmt'
            }
        }

        stage('terraform plan') {
            when {
                expression {
                    params.ENVIRONMENT == 'DEV'
                }
            }

            steps {
                sh 'terraform plan'
            }
        }

        stage('terraform apply') {
            when {
                 branch 'main'
                }

            when {
                expression {
                    params.ENVIRONMENT == 'PROD'
                }
            }
            steps {
                sh 'terraform apply --auto-approve'
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Pipeline completed successfully'
        }

        failure {
            echo 'FAILURE: Pipeline failed'
        }

        aborted {
            echo 'ABORTED: Build was stopped'
        }

        // always {
        //     cleanWs()
        //     echo 'cleanup the workspace'
        // }
    }
}
