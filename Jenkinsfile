pipeline {
    agent {
        docker {
            image 'python:3.11-slim'
        }
    }

    stages {
        stage('Install dependencies') {
            steps {
                sh 'pip install pytest --quiet'
            }
        }
        stage('Run tests') {
            steps {
                sh 'pytest test_app.py -v'
            }
        }
        stage('Report') {
            steps {
                echo 'All tests passed — ready to deploy'
            }
        }
    }

    post {
        failure { echo 'Pipeline failed — tests did not pass' }
        success { echo 'Pipeline completed successfully' }
    }
}