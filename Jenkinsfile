pipeline{
    agent any
    stages{
        stage("git checkout"){
            steps{
                git credentialsId: 'gitcred', url: 'https://github.com/SHAIKASIFAHAMED/java-hello-world-webapp.git'
            }
        }
        stage("maven build"){
            steps{
                sh 'mvn clean package'
                sh "mv target/*.war target/myapp.war"
            }
        }
        stage("tomcat deploy"){
            steps{
                sshagent(['ec2-cred']) {
                   sh "scp -o Stricthostkeychecking=no target/myapp.war ubuntu@172.31.31.22:/var/lib/tomcat8/webapps"
                      }
            }
        }
    }
}
