pipeline {
    agent any
    tools{
        git 'Default'
        }
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
        }
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker')
            }

    stages {
        stage('build') {
            steps {
                sh 'docker build -t jenkinsshailini/testrepo:test1'
            }
        }
        stage('Push'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIAL_PSW | docker login -u $DOCKERHUB_CREDENTIAL_USR --password-stdin'
                sh 'docker push jenkinsshailini/testrepo:test1'
            }
        }
    }
}
