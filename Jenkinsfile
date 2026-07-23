pipeline {
    agent any

    stages {

        stage('Clean Workspace') {
            steps {
        sh '''
        rm -rf practice-ansible
        rm -rf static
        '''
    }
}

        stage('Checkout Jenkinsfile') {
            steps {
                echo "Pipeline Started"
            }
        }
        
        stage('Clone Ansible Repo') {
            steps {
                sh '''
                git clone https://github.com/sainiyuvraj672-hub/practice-ansible.git
                '''
            }
        }

        stage('Clone Static Repo') {
            steps {
                sh '''
                git clone https://github.com/sainiyuvraj672-hub/static.git
                '''
            }
        }

        stage('Copy Static into Ansible Repo') {
            steps {
                sh '''
                cp static/* practice-ansible/
                echo "After Copy"
                ls -la practice-ansible
                '''
            }
        }

        stage('Verify') {
            steps {
                sh '''
                pwd
                echo "Workspace"
                ls -la

                echo "Ansible Repo"
                ls -la practice-ansible

                echo "Static Repo"
                ls -la static
                '''
            }
        }

        stage('Copy files to Ansible Server') {
            steps {
                sh '''
                scp -r practice-ansible/* root@192.168.29.243:/root/ansible/
                '''
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                sh ''' 
                ssh root@192.168.29.243 \
                "cd /root/ansible && ansible-playbook -i inventory setup.yml"
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                ssh root@192.168.29.243 \
                "cd /root/ansible"
                '''
            }
        }

    }

    post {
        always {
            echo "Pipeline Finished"
        }
        success {
            echo "Deployment Successful"
        }
        failure {
            echo "Deployment Failed"
        }
    }
}
