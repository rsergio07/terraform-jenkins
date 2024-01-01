pipeline {
    agent any
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
                    withCredentials([usernamePassword(credentialsId: 'AWS_CREDENTIALS_ID', usernameVariable: 'rsergio-jenkins', passwordVariable: 'h|0qzG5)')]) {
                        input 'Deploy Infrastructure?'
                        sh 'terraform apply -auto-approve'
                    }
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
