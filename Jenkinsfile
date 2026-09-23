pipeline {
    agent {
        label 'swarn'
    }

    parameters {
        string(
            name: 'APP_NAME',
            defaultValue: 'myapp',
            description: 'Enter application name'
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
