pipeline {
    agent any
    environment {
        DOCKERHUB = credentials('dockerhub-creds')
        IMAGE = "your-dockerhub-username/your-repo:v1"
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/USERNAME/myrepo.git'
            }
        }
        stage('Build') {
            steps {
                sh "docker build -t ${IMAGE} ."
            }
        }
        stage('Login & Push') {
            steps {
                sh "echo ${DOCKERHUB_PSW} | docker login -u ${DOCKERHUB_USR} --password-stdin"
                sh "docker push ${IMAGE}"
            }
        }
    }
}

