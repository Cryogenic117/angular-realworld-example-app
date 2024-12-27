pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:20-alpine'
                    reuseNode true
                    args '-u root:root'
                }
            }
            steps {
                sh '''
                    yarn global add @angular/cli
                    yarn install
                    yarn ng build
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh '''           
                '''
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'dist/**'
        }
    }
}