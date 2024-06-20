 pipeline {
    agent { label 'aws' }
    environment {
        TOKENAWS = credentials('controller-ssh-key')
        GITHUB_TOKEN = credentials('github-token')  // Make sure this credential is configured in Jenkins
    }

    stages {
        stage('Install Git') {
            steps {
                sh 'sudo yum update -y'
                sh 'sudo yum install git -y'
            }
        }

        stage('Deploy to Testing') {
            steps {
                sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.167.22.242 "sudo dnf update -y; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@3.88.3.9 "sudo dnf update -y; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

        stage('Deploy to CCTB-ProductionEnv1') {
            steps {
                sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.152.167.227 "sudo dnf update -y; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

        stage('Deploy to CCTB-ProductionEnv2') {
            steps {
                sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.221.51.48 "sudo dnf update -y; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }
    }
}
