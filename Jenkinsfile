pipeline {
    agent any 
    tools{
        maven 'MAVEN33'
        jdk   'JAVA8'
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
                
            }
            post{
                success{
                    echo "Code quality check"
                    checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
                    echo "publish juni report"
                    junit '**/surefire-reports/*.xml'
                    echo "Archive Artifact"
                    archiveArtifacts '**/webapp.war'
                }
            }
        }

        stage('Deploy'){
            steps{
                echo "This is Deployment stage"
                build 'dev-deploy'
            }
        }

    }
}
