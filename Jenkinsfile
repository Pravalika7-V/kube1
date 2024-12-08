pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                    // Build the Docker image
                    echo 'Building Docker image...'
                    bat 'docker build -t my-kube3-chinna22 .'
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
                    // Use Jenkins credentials for Docker login
                    echo 'Logging into Docker Hub...'
                    withCredentials([usernamePassword(credentialsId: 'credential', 
                                                      usernameVariable: 'DOCKER_USERNAME', 
                                                      passwordVariable: 'DOCKER_PASSWORD')]) {
                        bat "docker login -u %DOCKER_USERNAME% -p %DOCKER_PASSWORD%"
                    }

                    // Tag and push the Docker image
                    echo 'Tagging and pushing Docker image...'
                    bat 'docker tag my-kube3-chinna docker.io/pravalika7/my-kube3-chinna22'
                    bat 'docker push docker.io/pravalika7/my-kube3-chinna22'

                    // Optional: Apply Kubernetes manifests
                    echo 'Applying Kubernetes manifests...'
                    bat 'kubectl apply -f my-kube1-deployment.yaml'
                    bat 'kubectl apply -f my-kube1-service.yaml'
                }
            }
        }
    }
}
