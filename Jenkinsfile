pipeline {

    agent {
        label 'ansible-agent'
    }

    stages {

        stage('Verify Agent') {
            steps {
                sh '''
                    hostname
                    java -version
                    ansible --version
                '''
            }
        }

        stage('Create VPC') {
            steps {
                sh '''
                    ansible-playbook playbook.yml
                '''
            }
        }
    }

    post {

        always {
            cleanWs()
        }

        success {
            echo 'VPC Created Successfully'
        }

        failure {
            echo 'Pipeline Failed'
        }
    }
}
