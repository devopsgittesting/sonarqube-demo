pipeline {
    agent any

    stages {
        stage ('BuildStage') {

            steps {
                fileExists 'pom.xml'
                withMaven(maven : 'maven_3_8_1') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_8_1') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_8_1') {
                    sh 'mvn deploy'
                }
            }
        }
            
          stage ('Archive Stage') {
            steps {
                withMaven(maven : 'maven_3_8_1') {
                   archiveArtifacts '**/target/jenkins-git-maven-web-0.5.0-SNAPSHOT.war'
                }
            }   
            
            
            
        }
    }
}
