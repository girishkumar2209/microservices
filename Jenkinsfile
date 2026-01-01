pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'girishcluster', contextName: '', credentialsId: 'k8-token', namespace: 'microservices', serverUrl: 'https://C73BEBC50F8799A0B53A07466BB08B3D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'girishcluster', contextName: '', credentialsId: 'k8-token', namespace: 'microservices', serverUrl: 'https://C73BEBC50F8799A0B53A07466BB08B3D.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n microservices"
                }
            }
        }
    }
}
