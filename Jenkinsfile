pipeline {
    agent any

    stages {

        stage('Terraform Format') {
            steps {
                sh 'terraform fmt -check'
            }
        }

    }
}
