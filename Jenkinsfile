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
        withSonarQubeEnv('sonarqube-9.7.1') {
          sh "mvn sonar:sonar"
        }
      }
    }
  }
}
