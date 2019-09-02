#!groovy

pipeline{
    agent any
    stages {
        stage ('checkout'){
            steps{
                checkout scm
                sh 'echo "checking out repo"'
            }
        }

        stage ('run docker'){
            steps{
                dir("${env.WORKSPACE}/docker"){
                    sh "pwd"
                    sh 'echo "stopping docker containers"'
                    sh 'docker ps -aq | xargs -r docker stop;'
                    sh 'echo "killing docker containers"'
                    sh 'docker ps -aq | xargs -r docker rm;'
                    sh 'echo "building docker image"'
                    sh 'docker build . -t "test"'
                    sh 'echo "trying to run docker"'
                    sh 'docker run -dit --name my_app  -p 8081:80 test'
                }
            }
        }

        stage ('test docker'){
            steps{
                script{
                    def response = sh(returnStdout: true, script: 'curl localhost:8081')
                    def validated = false
                    if ( "${response}" =~ /Moshe/){
                        validated = true
                    }

                    sh 'echo "${validated}"'
                }
            }
        }
    }
}

def validate_docker(url){
    
}