pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
    }
    stages {
        stage('Test') {
  	    steps {
    	        echo 'Testing...'
                sh 'mvn clean test'
  	    }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Build') {
            steps {
    	      echo 'Building...'
	      sh 'mvn clean package'
            }
            post {
              always {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
              }
            }
  	}
      stage('Deploy') {
  	steps {
    	    echo 'Deploying...'
  	}
      }
  }
}
