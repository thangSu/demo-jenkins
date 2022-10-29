pipeline{
    agent any 
    tools{
        maven 'maven3'
    }
    stages{
        stage('Git checkout'){
            steps{
               git 'https://github.com/thangSu/demo-asible-docker.git'
            }
        }
        stage("maven build"){
            steps{
                dir('helloworld'){
                    sh 'mvn clean package'
                    sh "mv webapp/target/*war webapp/target/myweb.war"
                } 
            }
        }
        stage("deloy-dev"){
            steps{
                sshagent(['private-key']) {
                dir('helloworld/webapp/target')
                sh """
                    scp -o StrictHostKeyChecking=no myweb.war ec2-user@10.0.1.174:/opt/tomcat8/webapps/

                    ssh ec2-user@10.0.1.174 /opt/tomcat8/bin/shutdown.sh
                    ssh ec2-user@10.0.1.174 /opt/tomcat8/bin/start.sh
                """
                }
            }
           
        }
    }
}