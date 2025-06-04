pipeline {
  agent any
  stages {
    stage('scm checkout') {
      steps {
          git 'https://github.com/Sneha-Demanna/maven-project.git'
        //git branch: 'master', url: 'https://github.com/kumargaurav039/maven-project.git'
      }
    }
    //   stage('package job') //valiadte, compile, test & then package
    // {
    //   steps {
    //       withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          
    //       withSonarQubeEnv(credentialsId: 'sonarconnection', installationName: 'sonar' ) {
    //          sh 'mvn package sonar:sonar'}
    //             }
          
    //       }
    //     }

    stage('package job') //valiadte, compile, test & then package
    {
      steps {
          // withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MVN_HOME', mavenSettingsConfig: '', traceability: true) {
          // sh 'mvn package'
          withMaven(globalMavenSettingsConfig: '', jdk: 'JDK_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
          sh 'mvn clean package'      
          }
          }
        }

 stage('create docker image') //valiadte, compile, test & then package
    {
      steps {
            sh 'docker build -t snehademanna/ethans_947:latest .'
          }
          }
        

     stage('push docker image') //valiadte, compile, test & then package
    {
      steps {
            withDockerRegistry(credentialsId: 'dockerHub') {
              sh 'docker push snehademanna/ethans_947:latest .'
            }
          }
      }
        
    //  stage('deploy job') //deploy
    // {
    //   steps {
    //   sshagent(['DEV_CICD']) {
    //     //sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.10.238:/usr/share/tomcat/webapps'
    //     sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@172.31.89.149:/usr/share/tomcat/webapps'

    //     }


    //       }
    //     }
          
      }

    
   


    }
