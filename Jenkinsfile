pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                sh '''
                rm -rf venv
                python3 -m venv venv
                chmod +x venv/bin/pip
                venv/bin/pip install --upgrade pip
                venv/bin/pip install -r requirements.txt
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                pkill -f app.py || true
                nohup venv/bin/python app.py > app.log 2>&1 &
                sleep 5
                '''
            }
        }
    }
}


