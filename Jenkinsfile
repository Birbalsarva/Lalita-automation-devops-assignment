pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from Git
                git branch: 'main', url: 'https://github.com/Birbalsarva/Lalita-automation-devops-assignment.git'
            }
        }

        stage('Build') {
            steps {
                // Install npm dependencies and build your app
                sh 'cd your-app-directory && npm install && npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Copy your app to the EC2 instance using SCP or any other method
                sh 'scp -i /path/to/your/keypair.pem -r your-app-directory ec2-user@your-ec2-instance-ip:/path/to/remote/directory'

                // SSH into the EC2 instance and start your app
                sh 'ssh -i /path/to/your/keypair.pem ec2-user@your-ec2-instance-ip "cd /path/to/remote/directory && npm install && npm start"'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}

