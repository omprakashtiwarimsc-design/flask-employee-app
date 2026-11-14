pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/omprakashtiwarimsc-design/flask-employee-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m pip install --no-cache-dir -r requirements.txt'
            }
        }

        stage('Run Flask Application') {
            steps {
                sh '''
                    JENKINS_NODE_COOKIE=dontKillMe nohup python3 app.py > flask.log 2>&1 &
                '''
            }
        }
    }

    post {
        success {
            echo 'Flask application started successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
