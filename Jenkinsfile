pipeline {

    agent any


    stages {
     stage('Install Python3') {

            steps {

                sh '''

                    apt-get update

                    apt-get install -y python3 python3-pip python3-venv

                    python3 --version

                    pip3 --version

                '''

            }

        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    python3 -m pip install -r requirements.txt
                '''
            }
        }


        stage('Run Flask Application') {
            steps {
                sh '''
                    nohup python3 app.py > flask.log 2>&1 &
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
