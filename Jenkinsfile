pipeline {
    agent {
        docker {
            image 'jenkins/agent:latest'
            args '--user root:root'
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                echo "Installing system dependencies..."
                sh '''
                # Update package lists
                sudo apk update
                
                # Install Python and pip
                sudo apk add --no-cache python3 py3-pip
                '''
            }
        }
        stage('Setup Python') {
            steps {
                echo "Setting up Python environment..."
                sh '''
                python3 --version
                python3 -m pip --version
                '''
            }
        }
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                python3 -m pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 hello.py
                python3 hello.py --name=Brad
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}