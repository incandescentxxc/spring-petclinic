pipeline {
  agent any

  tools {
    maven "Maven 3.8.6"
  }

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

    // stage ('Build') {
    //   steps {
    //       sh 'mvn clean install -Djacoco.skip=true'
    //   }
    // }


    stage ('Deploy') {
      steps {
          sh 'ansible-playbook -i webserver.hosts main.yml'
      }
    }
  }
}