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
                    sed -i "s/%%VERSION%%/1.$BUILD_NUMBER/" src/app/features/article/pages/home/home.component.html
                    cat src/app/features/article/pages/home/home.component.html
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