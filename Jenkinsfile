pipeline {
    agent any

    stages {
        stage ('BuildStage') {

            steps {
                fileExists 'pom.xml'
                
                    sh 'mvn compile'
                }
            }
        

        stage ('Testing Stage') {

            steps {
      
                    sh 'mvn clean test'
                }
            }
        


        stage ('Deployment Stage') {
            steps {
               
                    sh 'mvn package'
                }
            }
        
            
          stage ('Archive Stage') {
            steps {
             
                   archiveArtifacts '**/target/myweb-0.0.2-SNAPSHOT.war'
                }
            }   
           stage ('copy Stage') {
            steps {
             
                   sh " cp -rf '**/target/myweb-0.0.2-SNAPSHOT.war' /home"
                }
            }   
       
    }
}
