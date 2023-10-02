
currentBuild.displayName = "maven-web-application-#"+currentBuild.number
pipeline{
    agent any    
    stages {
        stage('continuous download') {
            steps {
                git 'https://github.com/khduss/maven-web-application-1.git'
            }
               
        }
        stage('continuous build') {
            steps {
                sh 'mvn clean install'
            }
        }
            stage('continuous upload/backup') {
            steps {
                sh 'sudo cp /root/var/lib/jenkins/workspace/maven-web-app-deploy/target/maven-web-application.war /opt/tomcat/webapps'
                sh 'sudo cp /root/var/lib/jenkins/workspace/maven-web-app-deploy/target/maven-web-application.war  /mnt/Backup_snapshot'
            }
               
        }
        stage('continuous Deliver on Webserver') {
            steps {
                sh 'ssh root@172.31.0.173'
                 sh 'scp /root/var/lib/jenkins/workspace/maven-web-app-deploy/target/maven-web-application.war root@172.31.0.173:/mnt/apache-tomcat-9.0.80/webapps'
            }
        } 
}
   
}
