pipeline {
    agent any
    parameters {
    string(name:'GIT_URL', description:'The URL of the source Git repository to use.', defaultValue: 'https://github.com/robertbotez/demo-app')
    string(name:'GIT_BRANCH', description:'The branch in the source Git repository to use.', defaultValue: 'main')
    }
    stages {
        stage("Checkout") {
            steps {
                checkout(changelog: false, poll: false, scm: [
                    $class: 'GitSCM',
                    branches: [
                        [name: params.GIT_BRANCH],
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
                            url: params.GIT_URL,
                        ],
                    ],
                ])
            }
        }
        stage('Build') {
            steps {
                sh ("./build-pipeline.sh")
            }
        }
        stage('Deploy') {
            steps {
                sh ("./deploy-pipeline.sh")
            }
        }
    }
}
