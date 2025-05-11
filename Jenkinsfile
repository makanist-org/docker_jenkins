pipeline {
    agent {
        docker {
            image 'docker:20.10.24-dind' // Alpine-based Docker-in-Docker image
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock --user root:root'
        }
    }

    triggers {
        pollSCM('* * * * *')
    }

    environment {
        PIP_NO_CACHE_DIR = 'off'
    }

    stages {
        stage('Install Python & Docker CLI') {
            steps {
                echo "Installing Python & Docker CLI..."
                sh '''
                apk update
                apk add python3 py3-pip docker-cli
                python3 --version
                pip3 --version
                docker --version
                '''
            }
        }

        stage('Setup Python Environment') {
            steps {
                echo "Setting up Python environment..."
                sh '''
                python3 --version
                pip3 --version
                '''
            }
        }

        stage('Build') {
            steps {
                echo "Installing dependencies..."
                sh '''
                cd myapp
                pip3 install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }

        stage('Docker Check (Optional)') {
            steps {
                echo "Checking Docker functionality..."
                sh '''
                docker pull hello-world
                docker images
                '''
            }
        }

        stage('Deliver') {
            steps {
                echo "Delivering build..."
                sh 'echo "doing delivery stuff..."'
            }
        }
    }
}
