
pipeline {
    options {
        buildDiscarder logRotator(numToKeepStr: '3')
        disableConcurrentBuilds()
    }
    agent any
    stages {
        stage('stage 1') {
            when {branch "develop"}
            steps {
                sh '''
                echo 'stage 1'
                '''
            }
        }
        stage('stage 2') {
            steps {
            sh '''
            echo 'stage 2'
            '''
            }
        }
    }
}
