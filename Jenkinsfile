pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "mehedihub/flarie-todo"
        DOCKER_CREDENTIALS_ID = "docker-hub-credentials"
        KUBECONFIG_CREDENTIALS_ID = "eks-kubeconfig"
        AWS_REGION = "us-east-1"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/mehediemon/flarie-todo.git'
            }
        }

        stage('Build and Test') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${DOCKER_IMAGE}:latest ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', "${DOCKER_CREDENTIALS_ID}") {
                        sh "docker push ${DOCKER_IMAGE}:latest"
                    }
                }
            }
        }

        stage('Deploy to EKS') {
            steps {
                script {
                    withCredentials([file(credentialsId: "${KUBECONFIG_CREDENTIALS_ID}", variable: 'KUBECONFIG')]) {
                        // Update image in the deployment manifest
                        sh """
                        sed -i 's|image:.*|image: ${DOCKER_IMAGE}:latest|g' deployment.yaml
                        """

                        // Deploy to EKS
                        sh """
                        kubectl apply -f deployment.yaml --kubeconfig=$KUBECONFIG
                        kubectl apply -f service.yaml --kubeconfig=$KUBECONFIG
                        """
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs.'
        }
    }
}
