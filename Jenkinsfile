pipeline {
    agent any
    def gitUrl='https://github.com/robertbotez/demo-app'

    stages {

        stage("SCM"){
          step([$class:'WsCleanup'])
            git branch: BRANCH_NAME, url: gitUrl
            }
        stage('Build') {
            steps {
                echo 'Building..'
                pwd
                ls
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
