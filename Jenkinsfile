pipeline {
  agent any

  stages {
    stage('ansible test') {
      agent {
        docker {
          image 'geerlingguy/docker-ansible:latest'
        }
      }
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