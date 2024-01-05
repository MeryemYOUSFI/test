pipeline {
    environment {
        registry = "meryemyousfi/ghm"
        dockerImage = ''
    }

    agent any

    stages {
        stage('Cloning our Git') {
            steps {
                script {
                    git branch: 'master', url: 'https://github.com/MeryemYOUSFI/test.git'
                }
            }
        }

        stage('Docker Login') {
            steps {
                script {
                    sh "echo 'Logging into Docker Hub'"
                    sh "docker login -u meryemyousfi -p dckr_pat_U_J3qrskC990UBFwEjQA48W8EEA"
                    
                }
            }
        }
      stage('Building Docker Image') {
            steps {
                script {
                    dockerImage = docker.build "${registry}:${BUILD_NUMBER}"
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    echo "Pushing Docker images to Docker Hub"
                        docker.image("meryemyousfi/ghm:${BUILD_NUMBER}").push()

                }
            }
        }
    }
}
