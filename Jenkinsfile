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

            }
        }

        stage('Build') {
            steps {
                echo "Installing dependencies..."

            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
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
