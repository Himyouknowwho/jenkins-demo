pipeline {
    agent any
    stages {
        stage('build dind-java image') {
            steps {
                sh 'docker build -f Dockerfile.dind.java -t ata-dind-java .'
            }
        }
    }
}