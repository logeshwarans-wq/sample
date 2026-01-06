pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t nginx-rootless .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f nginx-rootless || true
                docker run -d -p 80:80 --name nginx-rootless nginx-rootless
                '''
            }
        }
    }
}

