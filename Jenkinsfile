pipeline {
    agent any

    stages {
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
                sh 'terraform plan'
                sh 'hostname'
                sh 'whoami'
                
            }
        }
    }
}
