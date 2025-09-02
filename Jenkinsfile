jenkins: pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'git@github.com:olaniyikolawole744/git-gra-pro.git'
            }
        }
        stage('Host Website on Nginx') {
            steps {
                sh 'ansible-playbook playbook-nginx.yml -i inventory.yml --vault-password-file /var/lib/jenkins/.ssh/.vault_pass.txt'
            }
        }
        stage('Install and configure Prometheus, Grafana and Transporter') {
            steps {
                sh 'ansible-playbook playbook-monitor.yml -i inventory.yml  --vault-password-file /var/lib/jenkins/.ssh/vault_pass.txt'
            }
        }
    }
}
