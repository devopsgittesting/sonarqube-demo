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
             
                   archiveArtifacts '**/target/jenkins-git-maven-web-0.5.0-SNAPSHOT.war'
                }
            }   
           
            
       
    }
}
