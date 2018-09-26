pipeline {
    agent any
    options {
        timeout(time: 1, unit: 'HOURS') 
    }
    environment {
                              
        GIT_COMMITTER_EMAIL = """${sh(
                                  returnStdout: true,
                                  script: 'git log -n 1 --format=\'%an <%ae>\''
                              )}"""

        REPOSITORY_BASE_NAME = """${sh(
                                  returnStdout: true,
                                  script: 'git config --get remote.origin.url | cut -d "/" -f 5 | cut -d "." -f 1 | tr -d \'[[:space:]]\''
                               )}"""

    }

    stages {
      stage("Determine Environment") {
          agent {
            kubernetes {
              label 'jenkins-slave-pipeline'
              containerTemplate {
                name 'jenkins-slave'
                image 'latamautos/tools:jnlp-slave'
                ttyEnabled true
                command 'cat'
              }
            }
          }

          steps {
            sh "cat /etc/issue"
            sh "docker --version"
            sh "sleep 300"
          }
      }
    }

}
