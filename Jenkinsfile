pipeline {
    agent any
    environment {
        DOCKER_REPO="himyouknowwho/homelab"
        DOCKER_IMAGE_NAME="ata-dind-java"
        IMAGE_TAG="${DOCKER_REPO}:${DOCKER_IMAGE_NAME}-${env.BUILD_ID}"
    }
    stages {
        stage('build dind-java image') {
            steps {
                script {
                    
                    def customImage = docker.build("${IMAGE_TAG}", "-f Dockerfile.dind-java .")
                }
            }
        }
        stage('Test image') {
            steps {
                script {
                    docker.image("${IMAGE_TAG}").withRun("-it --privileged") {
                        sh 'docker run hello-world'
                    }
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry("", 'docker-hub-push-token')  {
                        docker.image("${IMAGE_TAG}").push()
                    }
                }
            }
        }
    }
}