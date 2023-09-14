pipeline {

    agent any
    stages {
        stage('Packaging/Pushing imagae') {
            agent {
                label 'master'
            }
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
