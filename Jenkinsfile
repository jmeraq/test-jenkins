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
          container('jenkins-slave') {
            sh "cat /etc/issue"
            sh "docker ps"
            sh "sleep 300"
          }
      }
    }

}
