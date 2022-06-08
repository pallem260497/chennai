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
      stage ('test') {
        steps {
          sshagent(['ec2-user']) {
           sh "cp target/webapp.war /home/ec2-user/"
          }
        } 
      }
      /*stage ('deploy') {
       # steps {
        #  sshagent(['ec2-user']) {
         #   sh "hostname -I"
          #  sh "scp target/webapp.war usr/share/apache-tomcat-9.0.63/webapps"
           # sh "sudo su -s /bin/bash tomcat"
            #sh "cp /home/ec2-user/webapp.war /usr/share/apache-tomcat-9.0.63/webapps"
          #}
        #}
     # }*/
   }
}



