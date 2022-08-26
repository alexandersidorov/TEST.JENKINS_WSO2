
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
        stage('wso2 cli vcs status') {
            steps {
                bat '''
                apictl vcs status -e dev -k
                '''
            }
        }
//         stage('wso2 cli dev login') {
//             steps {
//                 bat '''
//                 apictl login dev -u admin -p rj2slcxjexa3n5v5rssw -k
//                 '''
//             }
//         }
        stage('Deploy APIs To "dev" Environment') {
            steps {
                   bat '''
                   apictl set --vcs-source-repo-path "%appDir%\\TEST.JENKINS_WSO2-1.0.0" -k
                   apictl vcs deploy -e dev -k
                   '''
           }
       }
    }
}
