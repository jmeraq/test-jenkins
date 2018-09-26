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
    stage('Run maven') {
      steps {
        sh 'ls -l'
        sh 'mkdir host'
        container('maven') {
          sh 'ls -l'
          sh 'mkdir hostmaven'
          sh 'mvn -version'
        }
        container('busybox') {
          sh 'mkdir hostbusybox'
          sh 'ls -l'
          sh '/bin/busybox'
        }
      }
    }
  }
}
