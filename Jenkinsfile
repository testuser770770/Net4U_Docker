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
                }
                // sh 'echo "trying to run docker-compose up"'
                // sh 'docker-compose up'
                sh 'echo "trying to run docker build & docker run"'
                sh 'sudo docker build . -t "test"'
                sh 'sleep 3'
                sh 'echo "trying to run docker"'
                sh 'docker run -dit --name my_app  -p 8080:80 test'
            }
        }
    }
}