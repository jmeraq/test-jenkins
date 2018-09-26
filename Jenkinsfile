pipeline {
  agent {
    kubernetes {
      label 'mypod'
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
  - name: busybox
    image: busybox
    command:
    - cat
    tty: true
"""
    }
  }
  stages {
    stage('Inicio') {
      steps {
        sh 'mkdir host'
        sh 'ls -l'
        sh 'cat /etc/issue'
      }
    }

    stage('Maven') {
      steps{
        container('maven') {
            sh 'mkdir hostmaven'
            sh 'cat /etc/issue'
            sh 'ls -l'
            sh 'mvn -version'
          }
      }
    }

    stage('Busibox') {
      steps{
        container('busybox') {
            sh 'mkdir hostbusybox'
            sh 'ls -l'
            sh '/bin/busybox'
        }
      }
    }

    stage('Fin') {
      steps {
        sh 'cat /etc/issue'
        sh 'ls -l'
      }
    }
  }
}
