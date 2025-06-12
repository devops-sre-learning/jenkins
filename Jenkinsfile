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
        '''
      }
    }
    stage('Run Ansible Playbook on localhost') {
            steps {
                // Create a simple playbook and inventory
                sh '''
                    echo '[local]\nlocalhost ansible_connection=local' > inventory
                    cat <<EOF > playbook.yml
                    - hosts: localhost
                      connection: local
                      gather_facts: false
                      tasks:
                        - name: Print message
                          debug:
                            msg: "Hello from Ansible on localhost"
                    EOF
                '''

                // Run the playbook
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }
    }
}