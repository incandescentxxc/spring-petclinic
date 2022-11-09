 node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.projectKey=17646-petclinic"
    }
  }
}