pipeline {
    agent any

    environment {
        IMAGE_NAME = 'venkat834/portfolio'
    }

    stages {
      //  stage('Clone') {
        //    steps {
          //      git 'https://github.com/Venkat834/Portofolio.git'
        // }
        // }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
                    script {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }

        stage('Deploy to AWS') {
            steps {
                sh 'echo Deploying to AWS...' // Placeholder
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'echo Deploying to K8s...' // Placeholder
            }
        }
    }
}
