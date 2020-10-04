pipeline {
    agent { label "master"}
    environment {
        ECR_REGISTRY = "088674315177.dkr.ecr.us-east-1.amazonaws.com"
        APP_REPO_NAME = "david-repo/phonebook-app"
        AWS_REGION = "us-east-1"
    }
    stages {
        stage ('create ECR repo') {
            steps {
                echo 'creating ECR Repository....'
                sh """
                aws ecr create-repository \
                  --repository-name ${APP_REPO_NAME} \
                  --image-scanning-configuration scanOnPush=false \
                  --image-tag-mutability MUTABLE \
                  --region ${AWS_REGION}
                """
                sh 'docker build --force-rm -t "${ECR_REGISTRY}/${APP_REPO_NAME}:latest"  . '
                sh 'docker image ls'
                
            }
        }
        stage ("Build App Docker Image") {
            steps {
                echo 'Building App Docker Image'
            }
        }
        stage ("Push Docker Image to ECR Repo") {
            steps {
                echo 'Pushing App Docker Image to ECR Repo'
                sh 'aws ecr get-login-password --region ${AWS::Region} | docker login --username AWS --password-stdin ${ECR_REGISTRY}'
                sh 'docker push "${ECR_REGISTRY}/${APP_REPO_NAME}:latest"'
            }
        }
        stage ("Crete Ifrastucture for App") {
            steps {
                echo 'Creating Docker Swarm'
            }
        }
        stage ("Testing thr Infrastructure") {
            steps {
                echo 'testing if swarm is ok or Nok...'
            }
        }
        stage ("deploy the App on Docker-Swarm") {
            steps {
                echo 'Deploying App on Docker-Swarm'
            }
        }
        stage ("testing app if it is deployed or not") {
            steps {
                echo 'testing app if it is deployed or not'
            }
        }
    }
    post {
        always {
            echo 'deleting all local images'
            sh 'docker image prune -af'
        }
        failure {
            echo 'Deleting image repository on ECR due to failure'
        }
    }
}