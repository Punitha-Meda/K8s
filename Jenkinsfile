pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = "ap-south-1"
        CLUSTER_NAME = "puni"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Punitha-Meda/K8s.git'
            }
        }

        stage('Deploy to EKS') {
            steps {
                sh '''
                aws eks update-kubeconfig --region ap-south-1 --name puni
                kubectl apply -f deployment.yaml
                kubectl apply -f service.yaml
                '''
            }
        }
    }
}
