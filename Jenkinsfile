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
                    // Log in to Docker Hub
                    echo 'Logging into Docker Hub...'
                    bat 'docker login -u pravalika7 -p <your-docker-password>'

                    // Tag and push the Docker image
                    echo 'Tagging and pushing Docker image...'
                    bat 'docker tag my-kube3-chinna docker.io/pravalika7/my-kube3-chinna'
                    bat 'docker push docker.io/pravalika7/my-kube3-chinna'

                    // Apply Kubernetes manifests
                    echo 'Applying Kubernetes manifests...'
                    bat 'kubectl apply -f my-kube1-deployment.yaml'
                    bat 'kubectl apply -f my-kube1-service.yaml'
                }
            }
        }
    }
}
