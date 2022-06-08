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
          sshagent(['tomcat service']) {
            sh "hostname -I"
            sh "ip -a address"
            sh "scp -o StrictHostKeyChecking=no /home/ec2-user/webapp/target/webapp.war ec2-user@172.31.15.68/home/ec2-user/"
            sh "sudo su -s /bin/bash tomcat"
            sh "cp /home/ec2-user/webapp.war /usr/share/apache-tomcat-9.0.63/webapps"
          }
        } 
      }
   }
}



