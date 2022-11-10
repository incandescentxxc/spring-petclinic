// pipeline {
//   agent any
//   tools {
//     maven "Maven 3.8.6"
//   }
//   stages {
//     stage('Build Artifact') {
//       steps {
//         sh "mvn clean install"
//       }
//     }
//     stage('Sonarqube Analysis') {
//       steps {
//         withSonarQubeEnv('sonarqube-9.7.1') {
//           sh "mvn sonar:sonar -Dsonar.projectKey=petclinic"
//         }
//       }
//     }
//   }
// }
node {
  stage('SCM') {
    echo "start pulling repo"
    git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic'
  }
  stage('SonarQube analysis') {
    def scannerHome = tool 'SonarQube';
    withSonarQubeEnv('SonarQube-Server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=static-analysis-1 -Dsonar.java.binaries=. -Dsonar.sources=src/main,src/test -Dsonar.language=java"
    }
  }
//   stage("Quality gate") {
//         steps {
//             waitForQualityGate abortPipeline: true
//         }
//     }
//   stage("build jar file") {
//       echo "print the current path:"
//       sh "pwd"
//       sh "rm -rf .scannerwork"
//       echo "removed report task"
//       sh "./mvnw package"
//   }
}