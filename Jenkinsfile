pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    stages {
        stage('Build') {
            steps {
    	      echo 'Building...'
	      sh 'mvn clean package'
            post {
              always {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
              }
            }
  	}
      }
      stage('Test') {
  	steps {
    	    echo 'Testing...'
  	}
      }
      stage('Deploy') {
  	steps {
    	    echo 'Deploying...'
  	}
      }
  }
}
