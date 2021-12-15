pipeline {
    environment{
        image='nanditapal/git-jenkins-demo'
        registrycred='dockerhub'
        app=''
        pushreg='https://registry.hub.docker.com'
    }
    agent any
    stages {
        stage('Clone repo'){
            checkout scm
        }
        stage('Build') {
            steps {
                script{
                    app=docker.build image 
                }
            }
        }
        stage('Push'){
            steps{
                script{
                    docker.withRegistry pushreg dockerhub{
                    app.push()
                }
            }
            }
        }
    }
}
