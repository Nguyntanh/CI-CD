pipeline {
    agent any
    tools {
        maven 'Maven 3.9.10' // Tên Maven trong Global Tool Configuration
        jdk 'JDK 17.0.9'     // Tên JDK trong Global Tool Configuration
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Nguyntanh/CI-CD.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
    		steps {
        		sh 'mvn heroku:deploy'
    		}
	}
    }
    post {
        always {
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
        }
    }
}