pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout SCM
            }
        }
        
        stage('Terraform Init') {
            steps {
                sh 'terraform init -lock-timeout=10m'
            }
        }
        
        stage('Terraform Plan') {
            steps {
                sh 'cd my-project && terraform plan -out=tfplan'
            }
        }
        
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve tfplan'
            }
        }
        
        stage('Ansible Provisioning') {
            steps {
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }
    }
    
    
}

