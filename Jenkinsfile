//cambio en develop
pipeline {
    agent {
        kubernetes {
            label 'latamautos-tools'
            defaultContainer 'jnlp'
            containerTemplate{
                name 'tools'
                image 'latamautos/tools:kubernetes'
                workingDir '/home/jenkins'
                ttyEnabled true
                command 'cat'
                args ''
            }
        }
    }
    stages {
        stage('Run Docker') {
            steps {
                sh 'mkdir host'
                container('tools') {
                    sh 'mkdir hostdocker'
                    sh 'docker ps'
                    sh 'ls -l'
                }
            }
        }
        stage('Run Node and npm') {
            steps {
                container('tools') {
                    sh 'mkdir hostnodejs'
                    sh 'nodejs --version'
                    sh 'npm --version'
                    sh 'ls -l'
                }
            }
        }

        stage('Run Git') {
            steps {
                container('tools') {
                    sh 'mkdir hostgit'
                    sh 'git --version'
                    sh 'ls -l'
                }
            }
        }
        
        stage('Run SBT') {
            steps {
                container('tools') {
                    sh 'mkdir hostsbt'
                    sh 'sbt --version'
                    sh 'ls -l'
                }
            }
        }
        
        stage('Run HHVM') {
            steps {
                container('tools') {
                    sh 'mkdir hosthhvm'
                    sh 'hhvm --version'
                    sh 'ls -l'
                }
            }
        }
        
        stage('Run Java') {
            steps {
                container('tools') {
                    sh 'mkdir hostjava'
                    sh 'java --version'
                    sh 'ls -l'
                }
            }
        }
    }
}
