//cambio en develop
pipeline {
    agent {
        kubernetes {
            label 'kubernetes'
            defaultContainer 'jnlp'
            containerTemplate{
                name 'tools'
                workingDir '/home/jenkins'
                image 'latamautos/tools:kubernetes'
                ttyEnabled true
                command 'cat'
                args ''
            }
        }
    }
    stages{
        stage("Build"){
            steps {
                /*container("jnlp"){
                    withCredentials(bindings: [sshUserPrivateKey(credentialsId: 'jenkins_slave', \
                                                     keyFileVariable: 'jenkins_slave', \
                                                     passphraseVariable: '', \
                                                     usernameVariable: 'root')]) {
                            sh '''
                                ls -la
                                cat /etc/issue
                                git status
                                git --version
                                git remote set-url origin git@github.com:jmeraq/test-jenkins.git
                                git config --global user.email "jenkins@test.com"
                                git config --global user.name "Jenkins"
                                git tag -a "tag-test2" -m "tag-test2"
                                git push origin "tag-test2"
                            '''
                        } 
                 }*/
                container('tools'){
                    withCredentials(bindings: [sshUserPrivateKey(credentialsId: 'jenkins_slave', \
                                                 keyFileVariable: 'jenkins_slave', \
                                                 passphraseVariable: '', \
                                                 usernameVariable: 'root')]) {
                        sh '''
                            cat /etc/issue
                            hostname
                            which ssh
                            ls -la
                            ls -la .git/
                            git status
                            git --version
                        '''
                    }  
                }
            }
        }
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
