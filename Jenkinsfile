pipeline {
	agent {
			label 'master'
			}

	options { 
		//disableConcurrentBuilds() 
		buildDiscarder(logRotator(numToKeepStr: '10'))
		timestamps()	
		}

   stages {
      stage('Hello') {
         steps {
            script{echo 'Hello World'}
         }
      }
   }
}