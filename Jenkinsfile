pipeline{
    agent any
    
    stages{

        docker{
            image 'maven:3.8.7-eclipse-temurin-11'
            args '-v /root/.m2:/root/.m2'
        }
        
        stage('Deploy Backend'){
            steps{
                sh 'echo deploy backend'
                git credentialsId: 'github-account', url: 'https://github.com/willferal/java-backend'
                sh 'mvn clean package'
                sh 'echo $PWD'
/*                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'*/
            }
        }
        
        stage('Deploy prod'){
            steps{
                sh 'docker compose build'
                //sh 'docker compose up -d'
            }
        }
    }
}