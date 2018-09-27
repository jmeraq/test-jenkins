//cambio en develop
pipeline {
    agent {
        kubernetes {
            label 'latamautos-tools'
            defaultContainer 'jnlp'
            containerTemplate{
                    name 'tools'
                    image 'latamautos/tools'
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
                    sh 'mkdir hostsbt'
                    sh 'ls -l'
                    sh 'docker ps'
                }
            }
        }
        stage('Run Node') {
            steps {
                container('tools') {
                    sh 'node --version'
                }
            }
        }

        stage('Run Git') {
            steps {
                container('tools') {
                    sh 'git --version'
                }
            }
        }
    }
}
