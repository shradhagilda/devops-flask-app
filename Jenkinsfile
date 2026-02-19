pipeline {
    agent any

    stages {

        stage('Create Virtual Environment') {
            steps {
                sh 'python3 -m venv venv'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                . venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }

        stage('Stop Old App') {
            steps {
                sh 'pkill -f app.py || true'
            }
        }

        stage('Run App') {
            steps {
                sh '''
                . venv/bin/activate
                nohup python app.py > app.log 2>&1 &
                '''
            }
        }
    }
}

