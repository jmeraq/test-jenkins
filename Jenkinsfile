pipeline {
  agent any
  stages { 
   stage('Inicio') {
	   steps{
	   	sh 'cat /etc/issue'
		sh 'mkdir host'
		sh 'ls'
	   }
   }
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
	sh 'cat /etc/issue'
	sh 'mkdir hostubuntu'
	sh 'ls'
        container('ubuntu') {
	  sh 'mkdir ubuntuos'
	  sh 'ls'
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
	 sh 'cat /etc/issue'
	 sh 'mkdir hostdebian'
	 sh 'ls'
         container('debian') {
	   sh 'mkdir debianos'
           sh 'ls'
           sh 'cat /etc/issue'
         }
       } 
     }
  }
}

