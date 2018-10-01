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
                branch 'master'
            }
            steps{
                sh "echo 'Is Master'"
            }
        }
        
        stage("testdev"){
            when {
                branch 'develop'
            }
            steps{
                sh "echo 'Is Develop'"
            }
        }
    }
}
