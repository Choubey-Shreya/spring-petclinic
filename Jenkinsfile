pipeline{
    agent any
    tools{
        maven 'apache-maven-3.6.0'
    }
    stages{
        stage('SCM Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/Choubey-Shreya/spring-petclinic'
            }
        }
        stage('Build'){
            steps{
                sh './mvnw package'
                
            }
         }
        stage('Execute Ansible'){
            steps{
                ansiblePlaybook credentialsId: 'private-key1', disableHostKeyChecking: true, installation: 'ansible', inventory: 'dev.inv', playbook: 'apache.yml'
            }
        }
    }
}
