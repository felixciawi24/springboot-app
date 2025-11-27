pipeline {
    agent any

    stages {
        stage('Pull SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/felixciawi24/springboot-app.git'
            }
        }
        
        stage('Containerized Apps') {
            steps {
                sh'''
                docker build -t felixciawi/springboot-app:v3.0 .
                '''
            }
        }

        stage('Push to Registry') {
            steps {
                sh'''
                docker push felixciawi/springboot-app:v3.0
                '''
            }
        }

        stage('Deploy Apps') {
            steps {
                sh'''
                kubectl apply -f manifest/
                '''
            }
        }   
    }
}