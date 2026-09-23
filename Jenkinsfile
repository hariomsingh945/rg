pipeline {
    agent any

    parameters {

        // 1. String
        string(
            name: 'RESOURCE_NAME',
            defaultValue: 'my-vm',
            description: 'Enter infrastructure resource name'
        )

        // 2. Boolean
        booleanParam(
            name: 'TERRAFORM_APPLY',
            defaultValue: false,
            description: 'Run Terraform apply?'
        )

        // 3. Choice
        choice(
            name: 'ENVIRONMENT',
            choices: ['DEV', 'QA', 'PROD'],
            description: 'Select infrastructure environment'
        )

        // 4. Text
        text(
            name: 'CHANGE_DETAILS',
            defaultValue: 'Create infrastructure for application',
            description: 'Enter infrastructure change details'
        )

        // 5. Password
        password(
            name: 'INFRA_PASSWORD',
            defaultValue: '',
            description: 'Enter lab infrastructure password'
        )
    }

    stages {

        stage('Validate Parameters') {
            steps {
                echo "======================================"
                echo "Resource Name : ${params.RESOURCE_NAME}"
                echo "Environment   : ${params.ENVIRONMENT}"
                echo "Terraform Apply: ${params.TERRAFORM_APPLY}"
                echo "Change Details:"
                echo "${params.CHANGE_DETAILS}"
                echo "======================================"
                echo "Infrastructure password received"
            }
        }

        stage('Terraform Plan') {
            steps {
                echo "Running Terraform Plan..."
                echo "Environment: ${params.ENVIRONMENT}"
                echo "Resource: ${params.RESOURCE_NAME}"

                // Real project mein:
                // sh 'terraform init'
                // sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    if (params.TERRAFORM_APPLY) {

                        echo "Terraform Apply started..."
                        echo "Creating infrastructure..."
                        echo "Resource: ${params.RESOURCE_NAME}"
                        echo "Environment: ${params.ENVIRONMENT}"

                        // Real project mein:
                        // sh 'terraform apply -auto-approve'

                        echo "Infrastructure deployment completed"

                    } else {

                        echo "Terraform Apply skipped"
                        echo "Only Terraform Plan was requested"
                    }
                }
            }
        }
    }
}
