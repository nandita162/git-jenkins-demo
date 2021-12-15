node{
    environment{
        image='nanditapal/git-jenkins-demo'
        registrycred='dockerhub'
        app=''
        pushreg='https://registry.hub.docker.com'
    }
    agent any
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
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub'){
            app.push()
        }
    }
}
