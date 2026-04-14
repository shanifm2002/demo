pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                 git branch: 'main', url: 'https://github.com/shanifm2002/demo.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sshagent(['ec2-user']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no ec2-user@98.92.153.234 << EOF
                    cd /home/ec2-user
                    git pull origin main
                    sudo systemctl restart app
                    EOF
                    '''
                }
            }
        }
    }
}
