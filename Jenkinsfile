pipeline {
    agent any
    environment{
        app=''
        image=''
        pushreg='nanditapal/git-jenkins-demo'
        no='${env.BUILD_NUMBER}'
        bname='${env.BRANCH_NAME}'
    }
    stages {
        stage('Build') {
            steps {
                script{
                    sh '$no $bname'
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
