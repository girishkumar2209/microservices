pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'mycluster', contextName: '', credentialsId: 'k8-token', namespace: 'microservices', serverUrl: 'https://C255C39EBEE5DF7D6612E0017ACA172A.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'mycluster', contextName: '', credentialsId: 'k8-token', namespace: 'microservices', serverUrl: 'https://C255C39EBEE5DF7D6612E0017ACA172A.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n microservices"
                }
            }
        }
    }
}
