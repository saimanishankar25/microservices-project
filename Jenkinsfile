pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'SAI-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A8A90B6E8C9D645CACB6E297E4874272.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'SAI-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://A8A90B6E8C9D645CACB6E297E4874272.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
