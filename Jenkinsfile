pipeline {
  agent {
    docker {
      image 'geerlingguy/docker-ansible:latest'
      args '-v $HOME/.ssh:/root/.ssh:ro'
    }
  }

  stages {
    stage('Ansible Test') {
      steps {
        sh '''
          echo "✅ Checking Ansible versions..."
          ansible --version
          ansible-playbook --version
          ansible-galaxy --version
        '''
      }
    }
  }
}