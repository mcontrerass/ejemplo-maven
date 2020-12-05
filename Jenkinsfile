pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
            	sh 'mvn clean compile -e'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn clean test -e'
            }
        }
        stage('Jar') {
            steps {
         	sh 'mvn clean package -e'
            }
        }
	stage('SonarQube') {
	    steps {
	    	withSonarQubeEnv(installationName: 'sonar') {
			sh 'mvn org.sonarsourse.scanner.maven:sonar-maven-plugins:3.7.0.1746:sonar'
		}
	    }
	}
        stage('Run') {
            steps {
                sh 'mvn spring-boot:run &'
                sh 'sleep 60'
            }
        }
        stage('TestingApp') {
            steps {
                sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing'
            }
        }
    }
}
