pipeline {
    agent any
    environment {
        IMAGE_NAME = flask-app
        REPO_NAME = likhith08/python-app
    }
    options {
        // This disables the default SCM checkout
        skipDefaultCheckout(true)
    }
    stages {
        stage('Docker Login') {
            withCredentials([usernamePassword(credentialsId: 'docker_creds', passwordVariable: 'DOCKER_TOKEN', usernameVariable: 'DOCKER_USER')]) {
                // Log in using the token as the password
                sh "echo \$DOCKER_TOKEN | docker login -u \$DOCKER_USER --password-stdin"
                sh "echo Login to docker successful"
            }
        }
        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/kodekloudhub/jenkins-project.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }

        // stage('Create docker image') {
        //     steps {
        //         sh "docker build -t likhith08/python-app:${env.GIT_COMMIT} . "
        //     }
        // }

        // stage('Push docker image') {
        //     steps{
        //         sh "docker push likhith08/python-app"
        //     }
        // }
    }
}