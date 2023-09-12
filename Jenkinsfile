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
                // Copy your app to the EC2 instance using SCP
                sh 'scp -i /home/ubuntu/ssh_key/Bs.key -r your-app-directory ubuntu@3.106.58.108:/path/to/remote/directory'

                // SSH into the EC2 instance and start your app
                sh 'ssh -i /home/ubuntu/ssh_key/Bs.key ubuntu@3.106.58.108 "cd /path/to/remote/directory && npm install && npm start"'
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

