pipeline {
    agent any

    stages {
        stage("Clean workspace") {
            steps {
                cleanWs()
            }
        }
        stage("Checkout") {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/dev'], [name: '*/prod']], userRemoteConfigs: [[url: 'https://github.com/danielkayode/sample-site.git']]])
            }
        }
        stage("Docker Build") {
            steps {
                script {
                    sh "docker build -t kcaher/sample-site -f Dockerfile.dev ."
                }
            }
        }
    }
}
