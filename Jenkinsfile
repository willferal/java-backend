pipeline{
    agent any
    
    stages{
        
        stage('Deploy Backend'){
            steps{
                sh 'echo deploy backend'
                git credentialsId: 'github-account', url: 'https://github.com/willferal/java-backend'
                sh 'mvn clean package'
                sh 'echo $PWD'
/*                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'*/
            }
        }
        
        stage('verify'){
            steps{
                sh'''
                    curl --version
                    jq --version
                '''
            }
        }
        
        stage('Deploy prod'){
            steps{
                sh 'ifconfig'
                //sh 'docker compose up -d'
            }
        }
    }
}