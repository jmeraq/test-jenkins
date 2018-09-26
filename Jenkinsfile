pipeline {
  agent {
        kubernetes {
          label 'jenkins-slave'
          containerTemplates {
            container{
              name 'ubuntu'
              image 'ubuntu:18.04'
              ttyEnabled true
              command 'cat'
            }
          }
        }
      }
  stages {
    stage('Run ubuntu') {
      
      steps {
        container('ubuntu') {
          sh 'cat /etc/issue'
        }
      }
    }
  }
}
