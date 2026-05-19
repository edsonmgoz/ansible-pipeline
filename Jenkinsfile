pipeline {
    agent {
        docker {
            image 'alpine/ansible:2.20.0'
            args '-u root:root'
        }
    }
    stages {
        stage('ansible') {
            steps {
                sh 'whoami'
                sh 'ansible --version'
            }
        }
    }
}