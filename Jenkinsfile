pipeline {
    agent any
    
    tools { 
        maven 'Maven 3.0.5' 
        jdk 'jdk8'
        
    }

    environment {
        JAVA_HOME="/opt/bitnami/java"
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    archive "target/**/*"
                }
            }
        }
        stage ('Deploy'){
            steps {
                echo 'Code deployed.'
            }
        }

    }
}