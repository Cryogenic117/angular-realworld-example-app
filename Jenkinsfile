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
                    yarn global add @angular/cli
                    yarn install
                    yarn ng build
                '''
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: 'dist/**', followSymlinks: false, onlyIfSuccessful: true
        }
    }
}