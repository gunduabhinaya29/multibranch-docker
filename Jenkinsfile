pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 gunduabhinaya29/paytm:movie'
            }
        }
         stage('push') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'dockerhub-id') {
                         sh 'docker push gunduabhinaya29/paytm:movie '
                     }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 gunduabhinaya29/paytm:movie'
            }
        }
    }
}
