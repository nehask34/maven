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
                sshagent(['131e3021-7894-4110-9a03-6a0aa96fb5cb']) {
                     sh "scp pipeline/target/myweb.war ec2-user@13.232.33.145:/opt/tomcat/webapps" 
                }
            }
        }
    }
}
