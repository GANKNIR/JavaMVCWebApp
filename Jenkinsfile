pipeline {
   agent any 
   tools { 
        maven 'Maven-3.6.0' 
    
    }
 stages {
     stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '9e612bee-967f-4172-a07a-a36df0a85b62', url: 'https://github.com/GANKNIR/JavaMVCWebApp.git']]])
      }
    }
    stage('build') {
      steps {
        sh 'mvn clean install'
      }
    }
   stage('deploy') {
      steps {
     sh 'mv ${WORKSPACE}/target/greenhouse*.war ${WORKSPACE}/target/greenhouse.war' 
      sh 'cp ${WORKSPACE}/target/greenhouse.war /opt/tomcat/webapps/'
        }
  }
 }
} 
