pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/poonamv28/CICD-project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy to AWS EC2') {
            steps {
                sh 'scp -i cicdkey.pem app.py ec2-user@<44.201.177.185>:/home/ec2-user/'
                sh 'ssh -i cicdkey.pem ec2-user@<44.201.177.185> "python3 /home/ec2-user/app.py &"'
            }
        }
    }
}
