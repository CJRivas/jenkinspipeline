pipeline {
    agent any
     
    triggers {
         pollSCM('* * * * *') 
     }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        parallel{
            stage ('Deploy to Staging'){
                steps {
                    sh 'scp -i /home/jenkins/tomcat-demo.pem **/target/*.war ec2-user@35.166.210.154:/var/lib/tomcat7/webapps'
                }
            }

            stage ('Deploy to Production'){
                steps {
                    sh 'scp -i /home/jenkins/tomcat-demo.pem **/target/*.war ec2-user@34.209.233.6:/var/lib/tomcat7/webapps'
                }
            }
        }
    }
}