 node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=sqp_40dc28e24445135c786cb917d8c687ba8f5bcf63 -Dsonar.projectKey=17646-petclinic"
    }
  }
}