pipeline {
    agent any

    stages {
        stage('run-secuirty-tests') {
            steps {
                sh 'sudo docker run --rm vhmds/bandit .' 
            }
        }
        stage('build-the-image') {
            steps {
                sh 'sudo docker build -t vhmds/new-flask-app .'
            }
        }
        stage('secuirty-scans-on-image') {
            steps {
                sh 'sudo docker run --rm aquasec/trivy:0.18.3 vhmds/new-flask-app'
            }
        }
       stage('push-to-docker-hub') {
            steps {
                sh 'sudo docker push vhmds/new-flask-app'
            }
        } 
    }
}
