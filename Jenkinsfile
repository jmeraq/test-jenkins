pipeline {
    agent none

    stages {
        stage('build') {
            stages {
               stage('Demo') {
                   when {
                      branch 'master'
                   }
                   steps {
                       sh "echo ${GIT_BRANCH}"
                   }
               }
               stage('Production') {
                   when {
                      branch 'develop'
                   }
                   steps {
                       sh "echo ${GIT_BRANCH}"
                   }
               }
            }
        }
    }
}
