pipeline {
    agent any
    stages {
        options {
        // This disables the default SCM checkout
        skipDefaultCheckout(true)
        }
        stage('Checkout') {
            steps {
                git url: 'https://github.com/kodekloudhub/jenkins-project.git', branch: 'main'
                sh "ls -ltr"
            }
        }
    }
}