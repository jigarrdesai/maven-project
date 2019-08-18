pipeline {
    agent any 
    tools{
        maven 'maven3'
        jdk   'java8'
    }
    stages {
        stage('init'){
            steps{
                echo "This is initializing stage"
            }
        }

        stage('Build'){
            steps{
                echo "This is Build stage"
                sh label: '',script:'mvn clean package checkstyle:checkstyle'
                echo "Code quality check"
                checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                echo "publish juni report"
                junit '**/surefire-report/*.xml'
            }
        }

        stage('Deploy'){
            steps{
                echo "This is Deployment stage"
            }
        }

    }
}
