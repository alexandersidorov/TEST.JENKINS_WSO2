
pipeline {
    options {
        buildDiscarder logRotator(numToKeepStr: '3')
        disableConcurrentBuilds()
    }
    agent any
    environment {
        appDir = "${WORKSPACE}"
    }
    stages {
        stage('echo workspace') {
            steps {
                bat """
                echo %appDir%
                dir /a
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
                   apictl login dev -u admin -p rj2slcxjexa3n5v5rssw -k
                   apictl set --vcs-source-repo-path %appDir% -k
                   apictl vcs deploy -e dev -k
                   '''
           }
       }
    }
}
