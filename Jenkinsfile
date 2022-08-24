
pipeline {
    options {
        buildDiscarder logRotator(numToKeepStr: '3')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    agent any
    tools {
        maven 'mvn'
        jdk 'jdk-15.0.1'
        // avaliable jdk1.8.0_91, jdk9.0.4, jdk10.0.1, jdk-14.0.1, jdk11.0.2, jdk-13.0.2
    }
    environment {

    }
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
