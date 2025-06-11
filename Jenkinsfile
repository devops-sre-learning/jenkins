pipeline {
    agent any

    environment {
        // Prevent SSH prompt for unknown host keys
        ANSIBLE_HOST_KEY_CHECKING = "False"
    }

    stages {
        stage('Clone Public Ansible Repo') {
            steps {
                git url: 'https://github.com/devops-sre-learning/jenkins.git'
            }
        }

        stage('Run Ansible on Host') {
            steps {
                sshagent(['your-existing-ssh-cred-id']) {
                    sh '''
                        ssh -o StrictHostKeyChecking=no ryan@Ryan-ASUS.local \
                        "cd /home/ryan/.local/bin/ansible && ansible-playbook -i /home/ryan/jenkins/inventory/hosts.ini /home/ryan/jenkins/playbook.yml"
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
