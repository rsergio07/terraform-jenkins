pipeline {
    agent any
    
    environment {
        TF_VAR_aws_access_key = credentials('AWS_ACCESS_KEY_ID')
        TF_VAR_aws_secret_key = credentials('AWS_SECRET_ACCESS_KEY')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Terraform Init') {
            steps {
                script {
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    input 'Deploy Infrastructure?'
                    sh 'terraform apply -auto-approve'
                }
            }
        }

stage('Terraform Output') {
            steps {
                script {
                    def instanceIp = sh(script: 'terraform output -json instance_ip', returnStdout: true).trim()
                    echo "Instance IP: ${instanceIp}"
                }
            }
        }
    }
}
