pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                ./venv/bin/pip install --break-system-packages -r requirements.txt
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                pkill -f app.py || true
                nohup ./venv/bin/python app.py > app.log 2>&1 &
                '''
            }
        }
    }
}

