#!groovy
pipeline {
    agent none
   stages {     
    stage('Maven Install') {
      agent {         
       docker {          
         image 'maven:3.8.5'         
     }       
  }       
  steps {
       sh 'mvn clean install -Dcheckstyle.skip'
       }
     }
   }
 }