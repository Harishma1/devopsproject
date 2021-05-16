pipeline {
    tools {
	jdk 'myjava'
	maven 'mymaven'
	}
	agent none
    stages {
        stage('checkout') { 
		agent any
            steps {
                git 'https://github.com/Harishma1/devops.git' 
            }
        }
		
		stage('compile') {
		agent any
            steps {
                sh 'mvn compile'
            }
        }
				
	stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
		stage('MetricCheck') {
		agent any
            steps {
                sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
            }
        }
	stage('package') { 
            steps {
                sh 'mvn package'
                  }
        }
    }
}
