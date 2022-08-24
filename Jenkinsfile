
pipeline {
    options {
        buildDiscarder logRotator(numToKeepStr: '3')
        disableConcurrentBuilds()
    }
    agent any
    stages {
        stage('stage 1') {
            steps {
                bat """
                echo stage 1
                """
            }
        }
        stage('stage 2') {
            steps {
                bat """
                echo stage 2
                """
            }
        }
        stage('wso2 cli version') {
            steps {
                bat """
                apictl version
                """
            }
        }
        stage('wso2 cli get envs') {
            steps {
                bat '''
                apictl get envs
                '''
            }
        }
        stage('Deploy APIs To "dev" Environment') {
            steps {
                bat '''
                apictl login live -u admin -p rj2slcxjexa3n5v5rssw -k
                apictl import api -f ./wso2.zip -e dev -k
                '''
            }
        }
    }
}
