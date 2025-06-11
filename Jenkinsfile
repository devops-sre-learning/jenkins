pipeline {
  agent any

  stages {
    stage('Hello') {
      agent {
                docker {
                    image 'geerlingguy/docker-ansible:latest'
                    reuseNode true
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