pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CCD53077DA7F3A3F1033F6825970B0D3.yl4.eu-north-1.eks.amazonaws.com']]) {
                    sh "k apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CCD53077DA7F3A3F1033F6825970B0D3.yl4.eu-north-1.eks.amazonaws.com']]) {
                    sh "k get svc -n webapps"
                }
            }
        }
    }
}
