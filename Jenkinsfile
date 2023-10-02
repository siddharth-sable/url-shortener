pipeline {
    agent any
    
    stages {
        stage('Install Docker') {
            steps {
                sh 'curl -fsSL https://get.docker.com | sh'
                sh 'sudo usermod -aG docker ${USER}'
            }
        }
        
        stage('Install Docker Compose') {
            steps {
                sh 'sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                sh 'sudo chmod +x /usr/local/bin/docker-compose'
            }
        }
        
        stage('Build and Run Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
    
    post {
        always {
            stage('Cleanup') {
                steps {
                    sh 'docker-compose down'
                }
            }
        }
    }
}
