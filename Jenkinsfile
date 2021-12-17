pipeline {
    agent any
    environment{
        app=''
        image=''
        pushreg='nanditapal/git-jenkins-demo'
    }
    stages {
        stage('Build') {
            steps {
                script{
                    image=docker.build pushreg+":latest"
                }
            }
        }
        stage('Push'){
            steps{
                script{
                    docker.withRegistry('','dockerhub'){
                        image.push()
                    }
                }
            }
        }
    }
}