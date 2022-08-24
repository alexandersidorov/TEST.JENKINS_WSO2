
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
                envs=$(apictl get envs --format "{{.Name}}")
                if [ -z "$envs" ];
                    then
                            echo "No environment configured. Setting dev environment.."
                    else
                            echo "Environments :"$envs
                            if [[ $envs != *"dev"* ]]; then
                                echo "Dev environment is not configured. Setting dev environment.."
                            fi
                            if [[ $envs != *"local"* ]]; then
                                echo "Local environment is not configured. Setting dev environment.."
                            fi
                fi
                '''
            }
        }
    }
}
