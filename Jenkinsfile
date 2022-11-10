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
      def scannerHome = tool 'SonarQube-Scanner-4.7.0';
      withSonarQubeEnv('sonarqube-9.7.1') {
        sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=petclinic"
      }
    }
  }
}
