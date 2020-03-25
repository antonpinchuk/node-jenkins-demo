pipeline {
    agent any
    stages {
        stage('Tests') {
            steps {
                //script {
                //    docker.image('node:10-stretch').inside {
                        echo 'Building..'
                        sh 'npm install'
                        echo 'Testing..'
                        sh 'npm test'
                //    }
                //}
            }
        }
        stage('Build and push docker image') {
            steps {
                script {
                    def dockerImage = docker.build("antonml/node-demo:master")
                    docker.withRegistry('', 'demo-docker') {
                        dockerImage.push('master')
                    }
                }
            }
        }
    }
}