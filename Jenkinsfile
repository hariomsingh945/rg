pipeline {
    agent any

    stages {
        stage('test squence of pipeline') {
            steps {
                echo 'Step 1'
                echo 'step 2'
                echo 'Step 3'
              }
    }

        stage('azure-login') {
            steps {
                sh 'az login --service-principal --username 0c24aa36-553a-4bdd-9b2f-ad2b5b6759ef --password fi18Q~HoIsvTlhTORYu-kwmD7ywSYaL~6XTkHaLB --tenant 5b0a096e-00db-4f9f-b16b-f0f9f22167d6'
                sh 'az account set --subscription "c3a580e1-714e-45fe-919a-734f28fb67de"'
            }
        }
        stage('terraform init') {
            steps {
                sh 'terraform init'
                sh 'terraform fmt'   
            }
        }
        stage('terraform plan') {
            steps {
                sh 'terraform plan'
                
            }
        }
        stage('terraform apply') {
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

        always {
            echo 'ALWAYS: Pipeline execution finished'
        }
    }
}
