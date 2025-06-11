pipeline {
  agent any

  stages {
    stage('Ansible Test') {
      steps {
        script {
          docker.image('geerlingguy/docker-ansible:latest').inside('-v $HOME/.ssh:/root/.ssh:ro') {
            sh '''
              echo "✅ Running inside container..."
              ansible --version
              ansible-playbook --version
            '''
          }
        }
      }
    }
  }
}