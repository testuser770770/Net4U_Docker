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
                sh 'echo "setting CWD to docker dir"'
                dir("${env.WORKSPACE}/docker"){
                    sh "pwd"
                    sh 'echo "cleaning env with docker rm $(docker ps -aq)"'
                    sh 'docker ps -aq | xargs -r docker rm;'
                    sh 'echo "trying to run docker build & docker run"'
                    sh 'docker build . -t "test"'
                    sh 'echo "trying to run docker"'
                    sh 'docker run -dit --name my_app  -p 8081:80 test'
                }
            }
        }
    }
}