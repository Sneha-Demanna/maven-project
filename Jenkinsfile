pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
          git 'https://github.com/Sneha-Demanna/maven-project.git'
        //git branch: 'master', url: 'https://github.com/kumargaurav039/maven-project.git'
      }
    }

    stage('package job') //valiadte, compile, test & then package
    {
      steps {
          // withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          // sh 'mvn package'
          withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn package'      
          }
          }
        }

     stage('deploy job') //deploy
    {
      steps {
      sshagent(['DEV_CICD']) {
        //sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.10.238:/usr/share/tomcat/webapps'
        sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.89.149:/usr/share/tomcat/webapps'

        }


          }
        }
          
      }

    
   


    }
