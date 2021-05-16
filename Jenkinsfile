pipeline {
    tools {
	jdk 'myjava'
	maven 'mymaven'
	}
	agent none
    stages {
        stage('checkout1') { 
		agent any
            steps {
                git 'https://github.com/Harishma1/devopsproject.git' 
            }
        }
		
		stage('compile') {
		agent any
            steps {
                sh 'mvn compile'
            }
        }
				
	stage('Test') { 
		agent any
            steps {
                sh 'mvn test' 
            }
           
        }
		stage('MetricCheck') {
		agent any
            steps {
                sh 'mvn cobertura:cobertura'
            }
        }
	stage('package') { 
		agent any
            steps {
                sh 'mvn package'
                  }
        }
    }
}
