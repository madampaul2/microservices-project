pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1190560B07171BAC53D0BC1B8642DF34.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1190560B07171BAC53D0BC1B8642DF34.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
