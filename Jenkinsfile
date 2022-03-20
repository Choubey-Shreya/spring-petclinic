pipeline{
    agent any
    tools{
        maven 'apache-maven-3.8.5'
    }
    
    stages{
       
       stage('GetCode'){
            steps{
                git branch: 'main', url: 'https://github.com/Choubey-Shreya/spring-petclinic.git'
                echo 'HELLO path'
                sh 'java --version'
                sh 'mvn --version'
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    echo "MAVEN_HOME = ${MAVEN_HOME}"
                '''
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
