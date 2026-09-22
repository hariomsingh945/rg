pipeline {
    agent any

    stages {
        stage('terraform fmt') {
            steps {
                sh 'terraform init'
                sh 'terraform fmt'
                sh 'terraform validate'
                
            }
        }
    }
}
