pipeline {
    agent none
    stages {
        stage('Build & tests') {
            agent {
                docker {
                    image 'node:10-stretch'
                }
            }
            steps {
                echo 'Building..'
                sh 'npm install'
                echo 'Testing..'
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                node {
                    checkout scm
                    def customImage = docker.build("node-demo:${env.BUILD_ID}", "./Dockerfile")
                }
            }
        }
    }
}