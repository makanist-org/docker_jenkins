pipeline {
    agent { 
        node {
            label 'docker-agent-python'
            }
      }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Setup Python') {
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

        stage('Deliver') {
            steps {
                echo "Delivering build..."
                sh 'echo "doing delivery stuff..."'
            }
        }
    }
}
