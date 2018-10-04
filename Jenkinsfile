pipeline {
    agent any
    environment{
        GIT_BRANCH = """
                ${sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD')}

        """
    }
    stages{
        stage("test"){
            steps{
                sh "echo '${GIT_BRANCH}'"
                sh "git rev-parse --abbrev-ref HEAD"
            }
        }
        
        stage("testprod"){
            when {
                expression {
                    return sh(script: "git rev-parse --abbrev-ref HEAD", returnStdout: true).trim() == "master"
                }
            }
            steps{
                sh "echo 'Is Master'"
            }
        }
        
        stage("testdev"){
            when {
                expression {
                    return sh(script: "git rev-parse --abbrev-ref HEAD", returnStdout: true).trim() == "HEAD"
                }
            }
            steps{
                sh "echo 'Is Develop'"
            }
        }
    }
}
