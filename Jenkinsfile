pipeline{
    agent any
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