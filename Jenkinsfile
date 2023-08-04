pipeline {

    agent any

    environment {
        MYSQL_ROOT_LOGIN = credentials('mysql')
    }
    stages {
        stage('Packaging/Pushing imagae') {

            steps {
                withDockerRegistry(credentialsId: 'dockerhub', url: 'https://index.docker.io/v1/') {
                    sh 'docker build -t phamvuphuong98/test-cicd .'
                    sh 'docker push phamvuphuong98/test-cicd'
                }
            }
        } 
    }
    post {
        // Clean after build
        always {
            cleanWs()
        }
    }
}