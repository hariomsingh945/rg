pipeline {
    agent {
        label "agenthari"
    }

    stages {
        stage('terraform fmt') {
            steps {
                sh 'terraform fmt'
            }
        }
        stage('terraform validate') {
            steps {
                sh 'terraform validate'
    }
}
    }
}
