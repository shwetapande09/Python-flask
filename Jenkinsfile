Pipeline {
    agent any
    environment{
        REGISTRY_URL ="https://index.docker.to/v1/"
        IMAGE_NAME   ="pandeshweta55/python-flask-app"
        CREDS_ID     ="dockerhub-creds"
    }
    stages{
        stage("Build docker image"){
            steps{
                   sh 'docker image build -t $IMAGE_NAME .'
                   sh 'docker image ls'
            }
        }
        stage("Push docker image into registry"){
        steps{
            script{
                docker.withRegistry("${REGISTRY_URL}", "${CREDS_ID}"){
                    echo "verify login details"
                    sh 'docker image push $IMAGE_NAME'
                }
            }
        }
    }
   }
}