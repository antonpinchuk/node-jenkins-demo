pipeline {
    agent any
    stages {
        stage('Build & tests') {
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
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                script {
                    def customImage = docker.build("node-demo:master")
                    //customImage.push("master")
                }
            }
        }
    }
}