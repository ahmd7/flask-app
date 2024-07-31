pipeline {
    agent any

    stages {
        stage('run-secuirty-tests') {
            steps {
                catchError{
                sh 'sudo docker run --rm vhmds/bandit app.py || true' 
                }
            }
        }
        stage('build-the-image') {
            steps {
                sh 'sudo docker build -t vhmds/new-flask-app .'
            }
        }
        stage('secuirty-scans-on-image') {
            steps {
                catchError{
                sh 'sudo trivy image vhmds/new-flask-app'
                }
            }
        }
       stage('push-to-docker-hub') {
            steps {
                sh 'sudo docker push vhmds/new-flask-app'
            }
        } 
    }
}
