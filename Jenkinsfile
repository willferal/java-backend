pipeline{
    agent any
    
    
    
    stages{
        stage('Deploy Backend'){
            steps{
                sh 'echo deploy backend'
                sh 'apt-get update && apt-get install -y maven'
                git credentialsId: 'github-account', url: 'https://github.com/willferal/java-backend'
                sh 'mvn clean package'
                sh 'echo $PWD'
/*                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'*/
            }
        }
        
        stage('Deploy prod'){
            steps{
                sh '/usr/bin/docker --version'
                //sh 'su - docker -c docker compose ps' 
                //sh 'docker compose up -d'
            }
        }
    }
}