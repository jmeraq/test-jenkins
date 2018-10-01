pipeline {
    agent any
    environment{
        GIT_BRANCH = """
                sh(returnStdout: true, script: "git rev-parse --abbrev-ref HEAD") 
        """
    }
    stages{
        stage("test"){
            steps{
                sh "echo 'hola'"
            }
        }
    }
}
