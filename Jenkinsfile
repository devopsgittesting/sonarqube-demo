pipeline {
    agent any

    stages {
        stage ('BuildStage') {

            steps {
                fileExists 'pom.xml'
                
                    sh 'mvn compile'
                    sh 'mvn clean install -Dv=${BUILD_NUMBER}'
                }
            }
        

        stage ('Testing Stage') {

            steps {
      
                    sh 'mvn clean test '
                }
            }
        


        stage ('Deployment Stage') {
            steps {
                    sh 'mvn package'
                }
            }
        
            
          stage ('Archive Stage') {
            steps {
             
                archiveArtifacts '**/target/.war'
                }
            }   
             stage ('Deploy on Webserver Stage') {
            steps {
             
                   sh "sudo cp -rf /var/lib/jenkins/workspace/Pipeline-Maven-jenkinsfile-git-artifacts/target/*.war /root/jenkins/apache-tomcat-9.0.48/webapps"
           
              }
            }   
      
    }
}
