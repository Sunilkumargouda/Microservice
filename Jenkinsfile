pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://92A92A7415BC5193B1ED7095C0906DC7.gr7.ap-southeast-1.eks.amazonaws.com']]) {
    
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://92A92A7415BC5193B1ED7095C0906DC7.gr7.ap-southeast-1.eks.amazonaws.com']]) {
    
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
