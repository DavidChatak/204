pipeline {
    agent { label "master"}
    environment {
        ECR_REGISTRY = "******"
    }
    stages {
        stage ('create ECR repo') {
            steps {
                echo 'creating ECR Repository....'


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
        }
        failure {
            echo 'Deleting image repository on ECR due to failure'
        }
    }



}