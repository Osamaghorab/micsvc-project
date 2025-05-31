pipeline {
    agent any
    stages {
        stage('Clone Repositories') {
            steps {

                dir('infra') {
                    git url: 'git@github.com:Osamaghorab/infra-tf-pb.git', credentialsId: 'your-repo-key', branch: 'your-branch'
                }


                dir('micsvc-manifests') {
                    git url: 'git@github.com:Osamaghorab/micsvc-manifests.git' credentialsId: 'your-repo-key', branch: 'your-branch'
                }
            }
        }
        stage('Provision EKS & S3') {
            steps {
                withAWS(credentials: 'your-aws-secret') {
                    dir('infra') {
                        sh 'terraform init'
                        sh 'terraform plan -out=tfplan'
                        sh 'terraform apply -auto-approve tfplan'
                    }
                }
            }
        }

        stage('Generate Main Backend Config & Connect With Remote State') {
            steps {
                withAWS(credentials: 'your-aws-secret') {
                    dir('infra') {
                        sh './generate_backend.sh'
                        sh 'terraform init'
                        sh 'terraform plan -out=tfplan'
                        sh 'terraform apply -auto-approve tfplan'
                    }
                }
            }
        }

        stage('Wait for EKS Provisioning') {
            steps {
                withAWS(credentials: 'your-aws-secret') {
                    dir('infra') {
                        sh '''
                        echo "Waiting for EKS cluster to become active"
                        while [[ "$(aws eks describe-cluster --name micsvc-eks-cluster --query 'cluster.status' --output text --region eu-north-1)" != "ACTIVE" ]]; do
                            echo "EKS is not ready yet, waiting"
                            sleep 20
                        done
                        echo "EKS cluster is now ACTIVE"
                        '''
                    }
                }
            }
        }

        stage('Deploy Microservices & Prom Stack') {
            steps {
                withAWS(credentials: 'your-aws-secret') {
                    dir('infra') {
                        sh 'ansible-playbook deploymicsvc.yaml'
                        sh 'ansible-playbook deploy-prom-stack.yaml'
                    }
                }
            }
        }
    }
}