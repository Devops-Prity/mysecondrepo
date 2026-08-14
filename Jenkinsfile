pipeline {
    agent any                      // run on any available agent
    environment {
        APP_NAME = 'myapp'
    }
    stages {
        stage('Checkout') {
            steps {
			   sh 'git clone url'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
				 sh 'mvn test'
            }
        }
               
        stage('Deploy') {
            when {
                branch 'main'      // deploy only from main branch
            }
            steps {
                sh 'scp target/myapp.war user@server:/opt/tomcat/webapps/'
            }
        }
    }
    post {
        success { echo 'Pipeline completed successfully!' }
        failure { echo 'Pipeline failed. Check logs.' }
    }
}
ptufg
