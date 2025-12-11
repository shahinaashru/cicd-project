pipeline {
    agent any

    stages {
        // Stage 1: Checkout Code from GitHub
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/shahinaashru/cicd-project/'
            }
        }

        // Stage 2: Deploy to Application Server
        stage('Deploy to App Server') {
            steps {
                // Use SSH credentials stored in Jenkins
                sshagent(credentials: ['appserver-key']) {
                    sh '''
                        echo "Copying index.html to Application Server..."
                        scp index.html ubuntu@13.53.173.171:/var/www/html/index.html
                    '''
                }
            }
        }
    }

    // Post actions executed after the pipeline stages
    post {
        success {
            echo "Deployment successful!"
        }
        failure {
            echo "Deployment failed!"
        }
    }
}
