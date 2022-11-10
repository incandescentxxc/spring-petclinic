node {
  stage('SCM') {
    echo "start pulling repo"
    git branch: 'main', url: 'https://github.com/incandescentxxc/spring-petclinic'
  }
  stage('SonarQube analysis') {
    def scannerHome = tool 'SonarQube-Scanner-4.7.0';
    withSonarQubeEnv('sonarqube-9.7.1') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=petclinic -Dsonar.java.binaries=. -Dsonar.sources=src/main,src/test -Dsonar.language=java"
    }
  }
  stage("build jar file") {
      sh "rm -rf .scannerwork"
      sh "./mvnw package"
  }
}