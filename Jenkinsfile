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
			sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
		}
	    }
	}
        stage('uploadNexus') {
            steps {
                // Subir artefacto a Nexus
            }
        }
    }
}
