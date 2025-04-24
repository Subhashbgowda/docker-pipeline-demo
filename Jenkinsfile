pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Subhashbgowda/docker-pipeline-demo'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t subhashbgowda/docker-demo-app:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                    sh 'docker push subhashbgowda/docker-demo-app:latest'
                }
            }
        }
    }
}
