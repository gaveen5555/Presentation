pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'ls'
                sh "chmod +x -R ${env.WORKSPACE}"
                sh './deploy.sh'
            }
        }
        stage('Test') {
            steps {
                sh 'ls'
                sh "chmod +x -R ${env.WORKSPACE}"
                sh './test.sh'
            }
        }
    }
    post {
        success {
            slackSend (color: '#00FF00', message: "*Staging Deployed*\n${env.JOB_NAME} [${env.BUILD_NUMBER}]'\n${env.BUILD_URL}")
        }
        failure {
            slackSend (color: '#FF0000', message: "*Staging Failed*\n${env.JOB_NAME} [${env.BUILD_NUMBER}]'\n${env.BUILD_URL}")
        }
    }
}