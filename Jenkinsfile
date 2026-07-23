pipeline {
    agent any

    stages {
        stage('hello') {
            steps {
                sh 'echo "Hello im $(hostname), were here to perform some thing from the github."'
            }
        }

        stage('script execution') {
            steps {
                sh 'chmod +x script.sh'
                sh 'bash script.sh'
            }
        }

        stage('Finish') {
            steps {
                echo "Pipeline done"
            }
        }

        stage('make file') {
            steps {
                // sh 'touch /root/file-pipeline.txt'
                // sh 'echo "hello yuvzie!!"> /root/file-pipeline.txt'
                sh 'touch file-pipeline.txt'
                sh 'echo "Hello Yuvzie!!" > file-pipeline.txt'
            }
        }
    }

    post {
        always {
            echo "Alway Executes."
        }
        success {
            echo "Pipeline executed sucessfully"
        }
        failure {
            echo "Pipeline execution failed"
        }
    }
}
