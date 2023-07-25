pipeline {
    agent any 
    stages {
      stage('SCM Checkout') {
        steps {
           git credentialsId: 'github'
           checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/sridhar-modalavalasa/Ansible-web-app']]])  
        }
      }  
      stage('Execute Ansible') {
        steps {
           ansiblePlaybook credentialsId: 'ubuntu-slaves-key', disableHostKeyChecking: true, installation: 'ansible-copsc', inventory: 'hosts', playbook: 'web-app.yml'
        }  
      }
    }
}
