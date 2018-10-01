pipeline {
    agent none
    environment{
        GIT_BRANCH = """${sh(
                        returnStdout: true, 
                        script: 'git rev-parse --abbrev-ref HEAD').trim()
                     }"""
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
