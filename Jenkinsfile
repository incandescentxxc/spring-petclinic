pipeline {
  agent any
  tools {
    maven "Maven 3.8.6"
  }
  stages {
    stage('Build Artifact') {
      steps {
        sh "mvn clean install"
      }
    }
    stage('Sonarqube Analysis') {
      steps {
        withSonarQubeEnv('SonarQube') {
          sh "mvn sonar:sonar -Dsonar.projectKey=17646-petclinic -Dsonar.host.url=http://localhost:9000"
        }
      }
    }
  }
}
