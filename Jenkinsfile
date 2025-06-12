pipeline {
  agent {
    docker {
      image 'geerlingguy/docker-debian12-ansible'
      args '-u 1000:1000 -e HOME=/tmp'
    }
  }

  environment {
    ANSIBLE_HOST_KEY_CHECKING = "False"
    ANSIBLE_TMPDIR = '/tmp'
  }

  stages {
    stage('Ansible Test') {
      steps {
        sh '''
          echo "✅ Running inside Docker container"
          ansible --version
          ansible-playbook --version
          ansible-playbook -i localhost playbook.yml
        '''
      }
    }
  }
}