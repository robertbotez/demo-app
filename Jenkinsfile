pipeline {
    agent any
    parameters {
    string(name:'GIT_URL', description:'The URL of the source Git repository to use.')
    string(name:'GIT_BRANCH', description:'The branch in the source Git repository to use.')
    string(name:'FILE_TO_SHOW', defaultValue:'', description:'The relative pathname of a file to print into the log.')
    }
    stages {
        stage("Checkout") {
            steps {
                checkout(changelog: false, poll: false, scm: [
                    $class: 'GitSCM',
                    branches: [
                        [name: 'main'],
                    ],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [
                        [
                            $class: 'RelativeTargetDirectory',
                            relativeTargetDir: 'src',
                        ],
                    ],
                    submoduleCfg: [],
                    userRemoteConfigs: [
                        [
                            url: 'https://github.com/robertbotez/demo-app',
                        ],
                    ],
                ])
            }
        }
        stage('Build') {
            steps {
                sh ("./build-and-deploy.sh")
            }
        }
        stage('Test') {
            steps {
                sh ("ls")
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
