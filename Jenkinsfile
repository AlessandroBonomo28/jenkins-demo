pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                sh 'pip3 install pytest --quiet --break-system-packages'
            }
        }
        stage('Run tests') {
            steps {
                sh 'python3 -m pytest test_app.py -v'
            }
        }
        stage('Report') {
            steps {
                echo 'All tests passed — ready to deploy'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed — tests did not pass'
        }
        success {
            echo 'Pipeline completed successfully'
        }
    }
}