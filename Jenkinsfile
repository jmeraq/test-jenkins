pipeline {
  agent any
  stages {
    stage('Run maven') {
      agent {
        kubernetes {
          label 'jenkins-slave'
          containerTemplate {
            name 'ubuntu'
            image 'ubuntu:18.04'
            ttyEnabled true
            command 'cat'
          }
          
          containerTemplate {
            name 'debian'
            image 'debian:9'
            ttyEnabled true
            command 'cat'
          }
        }
      }
      steps {
        container('ubuntu') {
          sh 'cat /etc/issue'
        }
        
        
        container('debian') {
          sh 'cat /etc/issue'
        }
      }
    }
  }
}
