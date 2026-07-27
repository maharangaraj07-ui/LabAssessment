pipeline {
    agent any

    environment {
        DOCKERHUB = credentials('dockerhub-creds')
        IMAGE = "maharangaraj07-ui/labassessment:v1"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/maharangaraj07-ui/LabAssessment.git',
                    credentialsId: 'github-pat'   
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE} ."
            }
        }

        stage('Login to Docker Hub') {
            steps {
                sh "echo ${DOCKERHUB_PSW} | docker login -u ${DOCKERHUB_USR} --password-stdin"
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push ${IMAGE}"
            }
        }
    }
}

