pipeline {
    agent any
    stages {
        stage("Build")
        {
            steps
            {
                script {
                    echo "INFO: Building docker image"
                    sh "docker build -t jenkins-nodejs-demo:latest ."
                    echo "INFO: Building docker image, Done"
                }
            }
        }

        stage("Deploy")
        {
            steps
            {
                script {
                    echo "INFO: Deploy the image"
                    // sh "ssh yxfan@host.docker.internal"
                    sh "docker rm -f jenkins-nodejs-demo || true"
                    sh "docker run --restart always -p 3000:3000 -d --name jenkins-nodejs-demo jenkins-nodejs-demo:latest"
                    echo "INFO: Deploy the image, Done"
                }
            }
        }
    }
}