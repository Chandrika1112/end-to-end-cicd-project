pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/chandrika1112/end-to-end-cicd-project'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-devops-app .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                docker stop devops-app || true
                docker rm devops-app || true
                docker run -d -p 80:80 --name devops-app cicd-devops-app
                '''
            }
        }
    }
}
