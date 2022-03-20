pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.5/bin"
    }
    
    stages{
       
       stage('GetCode'){
            steps{
                git branch: 'main', url: 'https://github.com/Choubey-Shreya/spring-petclinic.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
                
            }
         }
        stage('SonarQube analysis') {
        steps{
        withSonarQubeEnv('sonarqube-7.1') { 
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
