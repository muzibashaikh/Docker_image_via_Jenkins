// Jenkins-with-docker File Update 
pipeline {
    agent any
    environment {
        PATH = "C:\\Program Files\\Docker\\Docker\\Resources\\bin;${env.PATH}" // Adjust this path if Docker is installed elsewhere
    }
    stages {
        stage('Clean and Clone Repository') {
            steps {
                cleanWs()
                bat 'git clone https://github.com/muzibashaikh/Docker_image_via_Jenkins.git'
            }
        }
        stage('List Files') {
            steps {
                dir('Docker_image_via_Jenkins') {
                    bat 'dir'
                }
            }
        }
        stage('Build') {
            steps {
                dir('Docker_image_via_Jenkins') {
                    bat 'docker build -t mca2341/2341_muziba -f Dockerfile .'
                }
            }
        }
        stage('Login') {
            steps {
                bat 'docker login -u "mca2341" -p "muzi@dock82" docker.io'
            }
        }
        stage('Push') {
            steps {
                bat 'docker push mca2341/2341_muziba'
            }
        }
        stage('Run in Daemon Mode') {
            steps {
                bat 'docker rm -f my_container'
                // Running the Docker container in daemon mode
                bat 'docker run -d --name my_container mca2341/2341_muziba'
            }
        }
    }
}
