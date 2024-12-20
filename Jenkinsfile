pipeline {
    agent {
        docker {
            image 'node:20-alpine'
            reuseNode true
            args '-u root:root'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    yarn version
                '''
            }
        }
    }
}