pipeline {
    agent none
    stages {
        docker.image('node:10-stretch').inside {
            stage('Build & tests') {
                steps {
                    echo 'Building..'
                    sh 'npm install'
                    echo 'Testing..'
                    sh 'npm test'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                script {
                    def customImage = docker.build("node-demo:${env.BUILD_ID}", "./Dockerfile")
                    //customImage.push("master")
                }
            }
        }
    }
}