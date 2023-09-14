pipeline {
    agent {
        label 'dockeragent'
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
                sh 'git clone https://github.com/phamvuphuong98/test-cicd.git'
                sh 'cd test-cicd'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t phamvuphuong98/test-cicd:latest .'
            }
        }
        stage('login to docker hub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push phamvuphuong98/test-cicd:latest'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
