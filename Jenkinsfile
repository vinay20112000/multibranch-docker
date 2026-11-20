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
                sh 'docker tag image2 vinay20112000/paytm:bus'
            }
        }
        stage ('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        sh 'docker push vinay20112000/paytm:bus'
                    }
                }
            }
        }
        stage ('Deploy') {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 vinay20112000/paytm:bus'
            }
        }
    }
}
