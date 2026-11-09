pipeline{
    agent any 

    environment {
        PATH = "/opt/homebrew/bin:/usr/local/bin:${env.PATH}"
        DOCKER_USER='akshaymandalik'
        BACKEND_IMAGE="${DOCKER_USER}/yfc-backend"
        FRONTEND_IMAGE="${DOCKER_USER}/yfc-frontend"
        TAG = "${env.BUILD_NUMBER}"
    }
    stages {
        stage('Checkout'){
            steps{
                checkout scm 
            }
        }
        stage('Build Images'){
            steps{
                sh 'docker build -t $BACKEND_IMAGE:$TAG ./backend'
                sh 'docker build -t $FRONTEND_IMAGE:$TAG ./frontend'
            }
        }
        stage('Push Images'){
            steps{
                withCredentials([usernamePassword(credentialsId:'dockerhub',
                usernameVariable:'U',
                passwordVariable:'P')
                ])
                {
                    sh 'echo "$P" | docker login -u "$U" --password-stdin'
                    sh 'docker push $BACKEND_IMAGE:$TAG'
                    sh 'docker push $FRONTEND_IMAGE:$TAG'

                }
            }
        }
        stage('Deploy'){
            steps {
                sh 'kubectl set image deployment/backend backend=$BACKEND_IMAGE:$TAG -n yfc'
                sh 'kubectl set image deployment/frontend frontend=$FRONTEND_IMAGE:$TAG -n yfc'
                sh 'kubectl rollout status deployment/backend -n yfc'
                sh 'kubectl rollout status deployment/frontend -n yfc'
            }

        }
    }
}