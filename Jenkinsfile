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
                sh "target/*.war target/myweb.war"
            }        
        }
        
        stage("deploy to tomcat"){
            steps{
                sshagent(['tomcat']) {
                     sh """
                        scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.46.184:/opt/apache-tomcat-9.0.74/webapps/
                        
                        ssh ec2-user@172.31.46.184 /opt/apache-tomcat-9.0.74/bin/shutdown.sh
                        
                        ssh ec2-user@172.31.46.184 /opt/apache-tomcat-9.0.74/bin/startup.sh
                     """
                }
            }
        }
    }
}
