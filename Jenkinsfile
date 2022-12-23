pipeline {
    agent any
    stages{
        stage('Build') {
            steps {
                echo "Building"
                sh 'chmod 400 jenkins-key.pem'
                sh 'scp -T -o StrictHostKeyChecking=no -i jenkins-key.pem sample.war ec2-user@54.227.113.231:~'
            }
        }
        stage('Deploy') {
            steps{
                sh '''
                chmod 400 jenkins-key.pem
                ssh -T -o StrictHostKeyChecking=no -i jenkins-key.pem ec2-user@54.227.113.231 "sudo su; sudo mv sample.war /opt/tomcat/webapps"
            '''
            }
        }
    }
}
