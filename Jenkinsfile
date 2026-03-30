pipeline {
  agent any

  stages {
   stage('Install') {
    steps {
      sh 'npm install'
     }
    }

    stage('Build') {
      steps {
	sh 'echo "Building the app...""
	sh 'node index.js'
       }
      }

     stage('Archive') {
       steps {
	 archiveArtifacts artifacts:'**/*.js', fingerprint:true
	}
       }
      }
     }