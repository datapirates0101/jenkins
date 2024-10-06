pipeline {
    agent any
    environment {
        IMAGE_NAME = 'flask-app'
        REPO_NAME = 'likhith08/python-app'
    }
    stages {
        stage('Docker Login') {
            steps{
                    withCredentials([usernamePassword(credentialsId: 'docker_creds', passwordVariable: 'DOCKER_TOKEN', usernameVariable: 'DOCKER_USER')]) {
                    // Log in using the token as the password
                    sh "echo \$DOCKER_TOKEN | docker login -u \$DOCKER_USER --password-stdin"
                    sh "echo Login to docker successful"
                }
            }
        }

        stage('Debug') {
            steps {
                script {
                    echo "Current Git Commit: ${env.GIT_COMMIT}"
                }
            }
        }

        stage('Create docker image') {
            steps {
                sh "sudo docker build -t ${env.REPO_NAME}:${env.GIT_COMMIT} . "
            }
        }

        stage('Push docker image') {
            steps{
                sh "sudo docker push ${env.REPO_NAME}:${env.GIT_COMMIT}"
            }
        }
    }
}