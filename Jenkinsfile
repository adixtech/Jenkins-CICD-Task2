pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t jenkins-cicd-task2:latest .'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run -d --name jenkins-test -p 18081:80 jenkins-cicd-task2:latest'
                bat 'curl.exe -fsS http://localhost:18081'
                bat 'docker rm -f jenkins-test'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker rm -f jenkins-cicd-task2 2>nul'
                bat 'docker run -d --name jenkins-cicd-task2 -p 8081:80 --restart unless-stopped jenkins-cicd-task2:latest'
                bat 'curl.exe -fsS http://localhost:8081'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished. Check the stage results.'
        }
    }
}
