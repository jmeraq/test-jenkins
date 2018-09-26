pipeline {
  agent any
  stages {
    stage('Ubuntu Issue') {
      agent{
	    kubernetes {
	      label 'ubuntu'
	      containerTemplate {
	        name 'ubuntu'
	        image 'ubuntu:18.04'
	        ttyEnabled true
	        command 'cat'
	      }
	    }
	  }
      steps {
        container('maven') {
          sh 'cat /etc/issue'
        }
      }
    }
  	stage('Debian Issue') {
  	  agent{
	    kubernetes {
	      label 'debian'
	      containerTemplate {
	        name 'debian'
	        image 'debian:9'
	        ttyEnabled true
	        command 'cat'
	      }
	    }
	  }
      steps {
        container('debian') {
          sh 'cat /etc/issue'
        }
      }
  	}
  }
}

