pipeline {
    agent any
    // Environment variables
    environment {
        DOCKERHUB_CREDENTIALS = credentials('jenkins-dockerhub')
    }
    stages {
        stage('Example') {
            steps {
                sh 'echo Hello Docker!'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t paulsp93/jp-alpine:latest .'
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push paulsp93/jp-alpine:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout' // Simple logout
        }
    }
}
