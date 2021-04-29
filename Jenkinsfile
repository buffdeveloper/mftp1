pipeline {
  agent {
    node {
      label 'main'
    }

  }
  stages {
    stage('Echo Vars') {
      steps {
        sh '''echo ${GIT_COMMIT}
            echo ${GIT_CRED}
            echo ${TEMPLATE_REPO_URL}
            echo ${COMPLETE_PROJ_DIR}'''
      }
    }

    stage('Build Projects') {
      steps {
        sh '''/opt/tools/scripts/mftp_build.sh ${GIT_COMMIT} ${GIT_CRED} ${REPO_NAME} ${TEMPLATE_REPO_URL} ${LOCAL_TEMPLATE_DIR} ${TEMPLATE_DIR_NAME} ${PROJECT_PLACE_HOLDER} ${COMPLETE_PROJ_DIR} ${COMPLETE_PROJ_URL}
      '''
      }
    }

  }
  tools {
    maven 'Maven'
  }
  environment {
    GIT_CRED = credentials('ismail-kred')
    REPO_NAME = 'mftp1'
    TEMPLATE_REPO_URL = 'https://github.com/buffdeveloper/mftp_temp.git'
    LOCAL_TEMPLATE_DIR = '/opt/tools/mftp_project/mftp_temp'
    TEMPLATE_DIR_NAME = '/opt/tools/mftp_project/mftp_temp'
    PROJECT_PLACE_HOLDER = '_tn_'
    COMPLETE_PROJ_DIR = '/opt/tools/mftp_project/complete_projects'
    COMPLETE_PROJ_URL = 'https://github.com/buffdeveloper/complete_projects.git'

  }
}