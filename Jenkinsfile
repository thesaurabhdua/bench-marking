pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = 'your-docker-image-name'
        K8S_APP_NAME = 'your-kubernetes-app-name'
        K8S_APP_NAMESPACE = 'your-kubernetes-namespace'
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Pull latest changes
                    checkout scm

                    // Build Docker image
                    sh "docker build -t ${DOCKER_IMAGE_NAME} ."

                    // Push Docker image to a registry (e.g., Docker Hub)
                    sh "docker push ${DOCKER_IMAGE_NAME}"

                    // Get the latest image tag
                    def IMAGE_TAG = sh(script: "docker inspect --format='{{.Tag}}' ${DOCKER_IMAGE_NAME}", returnStdout: true).trim()

                    // Update the ArgoCD application manifest with the new image tag
                    sh "argocd app set ${K8S_APP_NAME} --namespace ${K8S_APP_NAMESPACE} --sync-option 'prune=true' --values=image.tag=${IMAGE_TAG}"

                    // Sync the ArgoCD application
                    sh "argocd app sync ${K8S_APP_NAME} --namespace ${K8S_APP_NAMESPACE}"
                }
            }
        }
    }
}
