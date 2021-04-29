pipeline {
  agent {
    node {
      label 'main'
    }

  }
  stages {
    stage('Initialize Tools') {
      steps {
        sh '''echo "PATH = ${PATH}"
            echo "M2_HOME = ${M2_HOME}"
            mvn -version
            echo ${AWS_ACCESS_KEY_ID}'''
      }
    }

    stage('Build Projects') {
      steps {
        sh '''mvn -version
      '''
      }
    }

  }
  tools {
    maven 'Maven'
  }
  environment {
    MAVEN_ARGS = '-Dmaven.deploy.skip=true -Dmaven.car.deploy.skip=false -Duser.name=${env.adminUser} -Dconsole.pass=${env.consolePassword} -Dserver.url=${env.devServerURL} -Dkeypass=${env.keystorePass} -Dkeystoredir=${env.keystorePath}'
    AWS_ACCESS_KEY_ID = credentials('bitbucket-creds')
  }
}