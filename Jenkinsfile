stage('Deploy to Kubernetes') {
            steps {
                // Point kubectl to your user's Kubernetes config and bypass validation
                bat 'set KUBECONFIG=C:\\Users\\batch1\\.kube\\config && kubectl apply -f deployment.yaml --validate=false'
            }
        }