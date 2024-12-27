pipeline {
    agent {
        docker {
            image 'node:20-alpine'
            reuseNode true
            args '-u root:root'
        }
    }
    environment {
        NETLIFY_SITE_ID = '7836bb3e-8eab-4841-94c6-599f3bbd9c61'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
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
        stage('Deployment') {
            steps {
                sh '''
                    yarn add netlify-cli -g
                    yarn netlify deploy --dir=dist/angular-conduit/browser --prod
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