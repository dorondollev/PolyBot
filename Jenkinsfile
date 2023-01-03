pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 352708296901.dkr.ecr.us-east-1.amazonaws.com
                docker build -t dorons-bot .
                docker tag dorons-bot:latest 352708296901.dkr.ecr.us-east-1.amazonaws.com/dorons-bot:latest
                docker push 352708296901.dkr.ecr.us-east-1.amazonaws.com/dorons-bot:latest
                '''
            }
        }
        stage('Trigger Deploy') {
            steps {
                build job: 'BotDeploy', wait: false, parameters: [
                    string(name: 'BOT_IMAGE_NAME', value: "352708296901.dkr.ecr.us-east-1.amazonaws.com"
        }
    }
}
