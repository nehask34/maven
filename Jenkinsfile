pipeline {
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
                sh "mv target/*.war target/myweb.war"
            }        
        }
        
        stage("deploy to tomcat"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '5e5f773a-56e5-43ae-89b8-8d6527edde95', path: '', url: 'http://13.232.33.145:8080/')], contextPath: 'sample', war: '**/*.war'
               }     
            }
        }
    }
}
