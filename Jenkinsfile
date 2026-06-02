pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git branch: 'main',
                url: 'https://github.com/76797185/Devops-Project.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t zoo-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop zoo-container || true
                docker rm zoo-container || true
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker run -d \
                --name zoo-container \
                -p 80:80 \
                zoo-website
                '''
            }
        }
    }
}
