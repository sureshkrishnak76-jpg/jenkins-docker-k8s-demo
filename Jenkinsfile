pipeline {
    agent any

    environment {
        KUBECONFIG = 'C:\\Users\\Suresh Krishna K\\.kube\\config'

        DOCKER = 'C:\\Users\\Suresh Krishna K\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe'

        KUBECTL = 'C:\\Users\\Suresh Krishna K\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sureshkrishnak76-jpg/jenkins-docker-k8s-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '"%DOCKER%" build -t jenkins-k8s-demo:1.0 .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                bat '"%DOCKER%" images jenkins-k8s-demo'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/jenkins-k8s-demo --timeout=120s'
            }
        }
    }
}
