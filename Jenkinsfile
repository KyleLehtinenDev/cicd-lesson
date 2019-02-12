pipeline {
    environment {
        DOCKERHUB_CRED = credentials('kldockerhub')
    }

    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh "docker build --no-cache -t kylelehtinendev/cicd-lesson:$BUILD_NUMBER ."
            }
        }
        stage('Login to Docker Hub with Credentials') {
            steps {
                sh "docker login -u $DOCKERHUB_CRED_USR -p $DOCKERHUB_CRED_PSW"
            }
        }
        stage('Push container to registry') {
            steps {
                sh "docker push kylelehtinendev/cicd-lesson:$BUILD_NUMBER"
            }
        }
        stage('Clean up local image') {
            steps {
                sh "docker rmi kylelehtinendev/cicd-lesson:$BUILD_NUMBER"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
