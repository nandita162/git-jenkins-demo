pipeline {
    environment{
        image='nandita162/git-jenkins-demo'
        registrycred='dockerhub'
        app=''
        pushreg='https://registry.hub.docker.com'
    }
    agent local
    stages {
        stage('Build') {
            steps {
                script{
                    app=docker.build image + ":$BUILD_NUMBER" 
                }
            }
        }
        stage('Push'){
            steps{
                script{
                    docker.withRegistry(pushreg, dockerhub){
                    app.push()
                }
            }
            }
        }
    }
}
