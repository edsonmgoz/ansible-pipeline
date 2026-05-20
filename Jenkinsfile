pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.20.0'
            args '-u root:root'
        }
    }
    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }
    stages {
        stage('ansible') {
            steps {
                sh 'whoami'
                sh 'ansible --version'

                sh 'env | sort'
                sh 'ansible-inventory --list'

                sshagent(credentials: ['amazon-linux-private-key']) {
                    // sh 'ansible server1 -i hosts -m ping -u ec2-user'
                    // sh 'ansible server1 -i hosts -m command -a "cat /etc/os-release" -u ec2-user'
                    // sh 'ansible server1 -i hosts -m yum -a "name=tree state=latest" -u ec2-user --become'
                    sh 'ansible-playbook -i hosts playbooks/server1_jboss.yml'
                }
            }
        }
    }
}