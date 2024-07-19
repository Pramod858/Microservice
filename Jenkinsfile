pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'K8S-Token', namespace: 'webapps', serverUrl: 'https://4F50EE4D0CAC201EE572C142407B1584.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'K8S-Token', namespace: 'webapps', serverUrl: 'https://4F50EE4D0CAC201EE572C142407B1584.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
