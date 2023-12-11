pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/manthanindane/justfortest.git']]])
            }
        }

        stage('BuildDockerImage') {
            steps {
                script {
                    bat 'docker build -t newimage .'
                }
            }
        }

        stage('changeimagetag') {
            steps {
                script {
                    bat 'docker tag newimage manthanindane/koibhi:tagname'
                }
            }
        }

        stage('PushDockerImage') {
            steps {
                script {
                    bat 'docker login -u manthanindane -p manthan1422'
                    bat 'docker push manthanindane/koibhi:tagname'
                }
            }
        }
    }
}
