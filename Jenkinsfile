pipeline {
    agent none
    environment{
        REPOSITORY_BASE_NAME = """${sh(
                                  returnStdout: true,
                                  script: 'git config --get remote.origin.url | cut -d "/" -f 5 | cut -d "." -f 1 | tr -d \'[[:space:]]\''
                               )}"""
                               
        
    }
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
