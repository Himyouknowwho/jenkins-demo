pipeline {
    agent any
    stages {
        stage('build dind-java image') {
            steps {
                script {
                    def customImage = docker.build("ata-dind-java:${env.BUILD_ID}", "-f Dockerfile.dind-java .")
                }
            }
        }
        stage('Test image') {
            steps{
                script {
                    customImage.inside {
                        sh 'docker run hello-world'
                    }
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    customImage.push()
                }
            }
        }
    }
}