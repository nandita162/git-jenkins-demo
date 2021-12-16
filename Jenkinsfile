pipeline {
    agent any
    environment{
        app=''
        image=''
        pushreg='nanditapal/git-jenkins-demo'
    }
    stages {
        stage('Git clone') {
            steps{
                sh 'sudo chown root:jenkins /var/run/docker.sock'
                git 'https://github.com/nandita162/git-jenkins-demo.git'
            }
        }
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
                        image.pull()
                    }
                }
            }
        }
    }
}