pipeline {
    agent any
    tools { nodejs "NodeJs" }
    stages {
        stage('Install & Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Create Image') {
            steps {
                sh 'docker build -t hondanho/text-compare .'
                // sh 'docker push hondanho/text-compare'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker rm $(docker stop $(docker ps -a -q --filter="name=text-compare"))'
                sh 'docker run --name text-compare -p 8008:8008 -d hondanho/text-compare'
            }
        }
    }
}
