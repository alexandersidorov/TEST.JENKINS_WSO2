
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
                print ("stage 1")
            }
        }
        stage('stage 2') {
            when {branch "develop"}
            steps {
                print ("stage 2")
            }
        }
    }
}
