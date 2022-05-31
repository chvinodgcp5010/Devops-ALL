pipeline {
  agent any 
  stages {
    stage ('fetch the code'){
      steps {
        git branch: 'paac', url: 'https://github.com/chvinodgcp5010/CICD-project-Nexus-and-Sonarqube.git' 
      }
    }
    stage ('build code'){
      steps {
        sh 'mvn install'
      }
    }
    stage ('test code'){
      steps {
        sh 'mvn test'
       }
    }
    stage('build && SonarQube analysis') {
       steps {
            withSonarQubeEnv('sonarqube_server') {                               //the name we gave on "configure system" of sonar server as sonarqube_server.
            // Optionally use a Maven environment you've configured already
            //withMaven(maven:'Maven 3.5') {                                    //If we use maven as tool use withMaven otherwise no need installed maven directly so directly mentioned mvn
            sh 'mvn clean package sonar:sonar'
           }
        }
     }
   }
 }
