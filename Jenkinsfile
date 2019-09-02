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
                sh 'echo "trying to run docker-compose up"'
                sh 'docker-compose up'
            }
        }
    }
}