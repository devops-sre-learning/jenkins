pipeline {
    agent any


    stages {
        stage('Clone Public Ansible Repo') {
            steps {
                git url: 'https://github.com/devops-sre-learning/jenkins.git'
            }
        }

        stage('Hello') {
            steps {
                    sh '''
                        ansible --version
                        ansible-playbook --version
                        ansible-galaxy --version
                    '''
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
