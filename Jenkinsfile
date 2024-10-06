pipeline {
    agent any
    options {
        // This disables the default SCM checkout
        skipDefaultCheckout(true)
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kodekloudhub/jenkins-project.git', branch: 'main'
                sh "ls -ltr"
            }
        }

        stage('Setup Environment') {
            steps {
                sh '''
                    python3 -m venv venv
                    /var/lib/jenkins/workspace/todo-app/venv/bin/python3 -m pip install -r requirements.txt
                    nohup /var/lib/jenkins/workspace/todo-app/venv/bin/python3 /var/lib/jenkins/workspace/todo-app/app.py &
                '''
            }
        }
    }
}