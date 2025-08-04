pipeline {
    agent any
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'plan', description: 'Git branch to build')
        booleanParam(name: 'RUN_APPLY', defaultValue: false, description: 'Run Terraform apply?')
    }
    
    stages {
        stage('Azure Login') {
            steps {
                withCredentials([azureServicePrincipal(
                    credentialsId: 'azure-sp',
                    subscriptionIdVariable: 'ARM_SUBSCRIPTION_ID',
                    clientIdVariable: 'ARM_CLIENT_ID',
                    clientSecretVariable: 'ARM_CLIENT_SECRET',
                    tenantIdVariable: 'ARM_TENANT_ID'
                )]) {
                    sh '''
                    echo "🔐 Logging in to Azure using Service Principal..."

                    az login --service-principal \
                        --username $ARM_CLIENT_ID \
                        --password $ARM_CLIENT_SECRET \
                        --tenant $ARM_TENANT_ID

                    az account set --subscription $ARM_SUBSCRIPTION_ID
                    '''
                }
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -var-file=terraform.tfvars'
            }
        }

        stage('Terraform Apply') {
            when {
                branch 'main'
            }
            steps {
                input message: 'Do you want to apply the Terraform changes?', ok: 'Apply'
                sh 'terraform apply -auto-approve -var-file=terraform.tfvars'
            }
        }
    }

    post {
        failure {
            echo "❌ Build failed on branch ${env.BRANCH_NAME}"
        }
    }
}
