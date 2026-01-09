pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 gunduabhinaya29/paytm:bus'
            }
        }
         stage('push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub-id') {
                         sh 'Docker push gunduabhinaya29/paytm:bus'
                     }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 gunduabhinaya29/paytm:bus'
            }
        }
    }
}
