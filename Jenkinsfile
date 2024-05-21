pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Ashoksana/automation-deployment-gopu.git'
            }
        }
        
        stage('Terraform Init') {
            steps {
                sh 'cd my-project && terraform init'
            }
        }
        
        stage('Terraform Plan') {
            steps {
                sh 'cd my-project && terraform plan -out=tfplan'
            }
        }
        
        stage('Terraform Apply') {
            steps {
                sh 'cd my-project && terraform apply -auto-approve tfplan'
            }
        }
        
        stage('Ansible Provisioning') {
            steps {
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }
    }
    
    
}

