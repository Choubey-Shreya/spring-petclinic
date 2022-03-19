pipeline{
    agent any
    environment {
        PATH = "$PATH:/usr/share/maven/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/Choubey-Shreya/spring-petclinic.git'
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
