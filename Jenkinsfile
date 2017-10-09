pipeline {
    agent any
    
    tools { 
        maven 'Maven 3.0.5' 
        jdk 'jdk8'
        
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archive "**/*.war"
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