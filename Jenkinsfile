pipeline {
  agent {
    docker {
      image 'geerlingguy/docker-ansible:latest'
      args '-v $HOME/.ssh:/root/.ssh:ro'
    }
  }

  environment {
    ANSIBLE_HOST_KEY_CHECKING = "False"
  }

  stages {
    stage('Ansible Test') {
      steps {
        sh '''
          echo "✅ Running inside Docker container"
          ansible --version
          ansible-playbook --version
        '''
      }
    }
  }
}
