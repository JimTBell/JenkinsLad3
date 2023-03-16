pipeline {
    agent any
    stages {
        stage('Cleanup Stage') {
            steps {
                sh "docker stop  \$(docker ps -q)  || echo \"No containers to stop\""
		sh "docker rm -f \$(docker ps -a -q) || echo \"No containers removed\""
		sh "docker rmi -f \$(docker images -q) || echo \"No images removed\""
            }
        }
        stage('Build Stage') {
            steps {
		sh "ls -al"
                sh "docker build -t jimtbell/task1 ."
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
