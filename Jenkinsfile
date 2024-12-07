pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    echo 'Building Docker image...'
                    bat 'docker build -t my-kube3-chinna .'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Placeholder for tests (if any)
                    echo 'Running tests...'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Log in to your Docker registry (if required)
                    echo 'Logging into Docker registry...'
                    bat 'docker login -u <username> -p <password>'

                    // Tag and push the Docker image
                    echo 'Tagging and pushing Docker image...'
                    bat 'docker tag my-kube3-chinna <your-registry>/my-kube3-chinna'
                    bat 'docker push <your-registry>/my-kube3-chinna'

                    // Apply Kubernetes manifests
                    echo 'Applying Kubernetes manifests...'
                    bat 'kubectl apply -f deployment.yaml'
                    bat 'kubectl apply -f service.yaml'
                }
            }
        }
    }
}
