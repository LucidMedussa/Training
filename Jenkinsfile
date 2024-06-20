 pipeline{
agent { label 'aws'}
environment{
TOKENAWS = credentials('controller-ssh-key')
}

    stages{
        stage('Deploy to Testing'){
            steps{
            sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.167.22.242 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

         stage('Deploy to Staging'){
            steps{
            sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@3.88.3.9 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

         stage('Deploy to CCTB-ProductionEnv1'){
            steps{
            sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.152.167.227 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }

        stage('Deploy to CCTB-ProductionEnv2'){
            steps{
            sh 'ssh -T -oStrictHostKeyChecking=no -i "$TOKENAWS" ec2-user@54.221.51.48 " sudo dnf update; sudo dnf install git -y; sudo dnf install -y httpd; sudo systemctl start httpd; sudo rm -Rf /var/www/html; sudo git clone https://github.com/LucidMedussa/Training /var/www/html"'
            }
        }
    }
 }