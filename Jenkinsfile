pipeline {
  agent any
  stages {
    stage('Run maven') {
      agent {
        kubernetes {
          label 'jenkins-slave'
          containerTemplate {
            name 'maven'
            image 'maven:3.3.9-jdk-8-alpine'
            ttyEnabled true
            command 'cat'
          }
        }
      }
      steps {
        container('maven') {
          sh 'mvn -version'
        }
      }
    }
  }
}
