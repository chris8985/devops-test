pipeline {
  agent any
  stages {
    stage('build a job') {
      parallel {
        stage('build a job') {
          steps {
            build(job: 'cicd-test', wait: true, quietPeriod: 8)
          }
        }
        stage('build shell') {
          steps {
            sh '''#!/bin/bash -x

cd ${WORKSPACE}

export GIT_COMMIT=`git rev-parse HEAD`
export GIT_SHORT_ID=${GIT_COMMIT:offset:5}
export TIME_STAMP=`date "+%Y%m%d%H%M"`
export PACKAGE_NAME_TAG=${TIME_STAMP}-${GIT_SHORT_ID}
echo `${PACKAGE_NAME_TAG}`
sleep 5'''
          }
        }
      }
    }
  }
}