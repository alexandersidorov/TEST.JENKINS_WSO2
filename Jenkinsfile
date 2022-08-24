
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
                set envs=(apictl get envs --format "{{.Name}})"
                echo "Environments :"%envs%
                '''
            }
        }
    }
}
