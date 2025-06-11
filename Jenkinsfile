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
                sshagent(['System']) {
                    sh '''
                        ansiblePlaybook become: true, credentialsId: 'super', installation: 'Ansible', inventory: '/home/ryan/jenkins/inventory/hosts.ini', playbook: '/home/ryan/jenkins/playbook.yml', vaultTmpPath: '/home/ryan/jenkins'
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
