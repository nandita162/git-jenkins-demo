pipeline {
    environment{
        registry='https://github.com/nandita162/git-jenkins-demo.git'
        registrycred='dockerhub'
        app=''
        pushreg='https://registry.hub.docker.com'
        dockerhubid='nanditapal'
    }
    agent any
    stages {
        stage('Build') {
            steps {
                script{
                    app=docker.build registry + ":$BUILD_NUMBER" 
                }
            }
        }
        stage('Push'){
            steps{
                script{
                    docker.withRegistry(pushreg, dockerhubid){
                    app.push()
                }
            }
            }
        }
    }
}
