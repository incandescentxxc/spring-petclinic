pipeline {
  agent any

  stages {
    stage('verify ansible') {
      steps {
        sh '''
          ansible --version
          ansible-playbook --version
          ansible-galaxy --version
        '''
      }
    }

    stage ('Build') {
      steps {
          withMaven(maven : 'maven') {
              sh 'mvn package'
          }
      }
    }


    stage ('Deploy') {
      steps {
          sh 'ansible-playbook -i webserver.hosts main.yml'
      }
    }
  }
}