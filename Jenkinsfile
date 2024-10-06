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
    }
}