pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven/bin:$PATH"
    }
    stages{
        stage("git checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/nehask34/maven.git'
            }
        }
        stage("maven build"){
            steps{
                sh "mvn clean package"
            }        
        }
    }
}
