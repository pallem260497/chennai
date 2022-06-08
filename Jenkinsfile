pipeline {
  agent any
  tools {
      jdk 'jdk11'
      git 'Default'
      maven 'maven'
  }
    stages {
      stage ('gitclone') {
        steps {
          git branch: 'master', url: 'https://github.com/pallem260497/chennai.git'
        } 
      }
      stage ('listGit') {
        steps {
          sh 'ls -lr'
        } 
      }
      stage ('maven') {
        steps {
          sh 'mvn clean package'
        } 
      }
      stage ('listmaven') {
        steps {
          sh 'ls -lr'
        } 
      }
      stage ('maven path') {
        steps {
          sh 'pwd'
        } 
      }
      stage ('deploy') {
        steps {
          sshagent(['ec2-user']) {
           sh 'scp /home/ec2-user/webapp/target /home/ec2-user/'
           sh 'sudo su -s /bin/bash tomcat'
           sh '/usr/share/apache-tomcat-9.0.63/webapps'
          }
        } 
      }
   }
}



