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
        sh '''mftp_build.sh ${GIT_COMMIT} ${GIT_CRED} ${REPO_NAME} ${TEMPLATE_REPO_URL} ${LOCAL_TEMPLATE_DIR} ${TEMPLATE_DIR_NAME} ${PROJECT_PLACE_HOLDER} ${COMPLETE_PROJ_DIR} ${COMPLETE_PROJ_URL}
      '''
      }
    }

  }
  tools {
    maven 'Maven'
  }
  environment {
    MAVEN_ARGS = '-Dmaven.deploy.skip=true -Dmaven.car.deploy.skip=false -Duser.name=${env.adminUser} -Dconsole.pass=${env.consolePassword} -Dserver.url=${env.devServerURL} -Dkeypass=${env.keystorePass} -Dkeystoredir=${env.keystorePath}'
    GIT_CRED = credentials('github-creds')
    REPO_NAME = 'mftp1'
    TEMPLATE_REPO_URL = 'https://github.com/buffdeveloper/mftp_temp.git'
    LOCAL_TEMPLATE_DIR = '/opt/tools/mftp_project/mftp_temp'
    TEMPLATE_DIR_NAME = '/opt/tools/mftp_project/mftp_temp'
    PROJECT_PLACE_HOLDER = '_tn_'
    COMPLETE_PROJ_DIR = '/opt/tools/mftp_project/complete_projects'
    COMPLETE_PROJ_URL = 'https://github.com/buffdeveloper/complete_projects.git'

  }
}