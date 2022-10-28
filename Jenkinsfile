pipeline {
    agent { label 'tuto' }
    
    environment {
        DOCKERHUB_CREDS = credentials('25')
    }

    stages {
        stage('Build') {
            steps {
                container('podman') {
                    script {
                        sh 'podman build -t docker.io/jmambrinventre/web-go:$BUILD_NUMBER -f Dockerfile'
                        sh 'podman login -u $DOCKERHUB_CREDS_USR -p DOCKER_CREDS_PSW'
                        sh 'podman push docker.io/jmambrinventre/web-go:$BUILD_NUMBER'
                    }
                }
                container('kubectl') {
                    script {
                        sh 'env'
                        sh 'kubectl get pod'
                    }
                container('fortune') {
                    script {
                        sh 'fortune'
                    }
                }
                }
            }
        }
    }
}
