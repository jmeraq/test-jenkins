pipeline {
    agent none
    stages {
        stage('build') {
            stages {
               stage('Demo) {
                   when {
                      branch 'master'
                   }
                   steps {
                       echo "Is Master"
                   }
               }
               stage('Production') {
                   when {
                      branch 'develop'
                   }
                   steps {
                       echo "Is Develop"
                   }
               }
            }
        }
    }
}
