pipeline{
    agent any
    
    
    stages{
        stage('Deploy Backend'){
            steps{
                sh 'echo deploy backend'
                // sh 'sudo rm /var/lib/apt/lists/lock && sudo rm /var/lib/dpkg/lock'
                // sh 'apt-get update && apt-get install -y maven'
                git credentialsId: 'github-account', url: 'https://github.com/willferal/java-backend'
                sh 'mvn clean package'
                sh 'echo $PWD'
/*                deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'*/
            }
        }
        
        stage('Deploy prod'){
            steps {
                // withEnv["PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin"]
                // sh '/usr/bin/docker --version'
                // echo "PATH is: $PATH"
                // sh 'docker run hello-world' // funciona
                sh 'docker-compose up -d' // não funciona
            }
        }
    }
}