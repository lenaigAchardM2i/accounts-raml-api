pipeline {
  agent any
  triggers{
    pollSCM('H/2 * * * *')
  }
  stages {
   stage('Build Application') {
      steps {
        sh 'mvn clean install'
      }  
    }
    stage('Deploy CloudHub') {
      environment {
        ANYPOINT_CREDENTIALS = credentials('319f83bd-4d18-474f-8315-49462ff81603')
      }
      steps {
        sh "mvn deploy -DmuleDeploy -Dcloud.env=Sandbox -DcloudhubAppName=account-api-lenaig -Dmule.version=4.6.1 -Dcloud.user=${ANYPOINT_CREDENTIALS_USR} -Dcloud.password=${ANYPOINT_CREDENTIALS_PSW}"
      }
    }
  }
}