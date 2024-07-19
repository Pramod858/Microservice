pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'K8S-Token', namespace: 'webapps', serverUrl: 'https://7395276879B8746F68CF62A0E196BEF7.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'K8S-Token', namespace: 'webapps', serverUrl: 'https://7395276879B8746F68CF62A0E196BEF7.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
