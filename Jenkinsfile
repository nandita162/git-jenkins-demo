node{
    def app{
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
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
                    app.push()
                }
            }
            }
        }
    }
    }
}
