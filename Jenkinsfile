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
                sh 'cd ./docker'
                sh 'echo "trying to run docker-compose up"'
                sh 'docker-compose up'
            }
        }
    }
}