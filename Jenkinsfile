pipeline {
   agent any
   stages {

        stage("Git checkout"){
          steps {
           git credentialsId: 'github-cred', url: 'https://github.com/demodevops2/java-hello-world-webapp.git'
    }
        }
          
           stage("Maven build"){
              steps {
               sh 'mvn clean package'
               sh "mv target/*.war target/myweb.war"  
              }
           }
      
      stage("Tomcat deploy"){
         steps {
          sshagent(['ec2-cred']) {
          sh "scp -o StrictHostKeyChecking=no target/myweb.war ubuntu@172.31.31.22:/var/lib/tomcat8/webapps"
}
         
         }
      
      
      }
           





}

}
