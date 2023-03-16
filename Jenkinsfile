pipeline {
    agent any
    stages {
        stage('Cleanup Stage') {
            steps {
                sh "docker stop  $(docker ps -q) && echo \"all contianers stopped\" || echo \"No contains to stop\""
		sh "docker rm -f \$(docker ps -a -q)"
		sh "docker rmi -f \$(docker images -q)"
            }
        }
        stage('Build Stage') {
            steps {
                sh "docker build -t jimtbell/task1 Task1"
            }
        }
        stage('Test') {
            steps {
                sh "docker images"
            }
        }
        stage('Deploy') {
            steps {
                sh "docker run -d -p 80:5500 --name task1 jimtbell/task1"
                sh "docker ps -a"
            }
        }
    }
}
