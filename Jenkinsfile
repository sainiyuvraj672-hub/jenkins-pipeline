pipeline {

    agent any

    stages {

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
