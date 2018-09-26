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
        sh 'cat /etc/issue'
        sh 'ls -l'
        sh 'mkdir host'
      }
    }

    stage('Maven') {
      steps{
        container('maven') {
            sh 'cat /etc/issue'
            sh 'ls -l'
            sh 'mkdir hostmaven'
            sh 'mvn -version'
          }
      }
    }

    stage('Busibox') {
      steps{
        container('busybox') {
            sh 'cat /etc/issue'
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
