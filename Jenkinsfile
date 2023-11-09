pipeline {
    agent any
    triggers {
  cron 'H/5 * * * *'
}

    tools{
        maven 'Apache Maven 3.2.5'
    }
    options {
  buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '2')
}


    stages {
        stage('Clone the repository') {
            steps {
               git credentialsId: 'Github_username_password', url: 'https://github.com/RAMDEVOPS23/build-deploy-tomcatserver.git'
            }
        }


        stage('Build the maven code') {
            steps {
            sh 'mvn clean install'
                 }
    }

stage('Deploy to tomcat') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat-cred', path: '', url: 'http://3.88.28.53:9090//')], contextPath: null, war: '**/*.war'
                 }
    }
}
}
