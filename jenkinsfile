pipeline {
    agent any

    stages {
        
        stage('Compile') {
            steps {
                dir("c:\\\\Mauricio\\\\Manuales\\\\DevOps\\\\USACH\\\\ejemplo-maven") {
                    sh 'mvn clean compile -e'
                }
            }
        }
        stage('Test') {
            steps {
                dir("c:\\\\Mauricio\\\\Manuales\\\\DevOps\\\\USACH\\\\ejemplo-maven") {
                    sh 'mvn clean test -e'
                }
            }
        }
        stage('Jar') {
            steps {
                dir("c:\\\\Mauricio\\\\Manuales\\\\DevOps\\\\USACH\\\\ejemplo-maven") {
                    sh 'mvn clean package -e'
                }
            }
        }
        stage('Run') {
            steps {
                dir("c:\\\\Mauricio\\\\Manuales\\\\DevOps\\\\USACH\\\\ejemplo-maven") {
                    sh 'mvn spring-boot:run &'
                    sh 'sleep 30'
                }
            }
        }
        stage('TestingApp') {
            steps {
                dir("c:\\\\Mauricio\\\\Manuales\\\\DevOps\\\\USACH\\\\ejemplo-maven") {
                    sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing'
                }
            }
        }
    }
}