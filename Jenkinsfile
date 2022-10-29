currentBuild.displayName = "thang-code-khong-co-sai#"+currentBuild.number
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
                sh """
                    scp -o StrictHostKeyChecking=no helloworld/webapp/target/myweb.war ec2-user@10.0.1.174:/opt/tomcat8/webapps/

                    ssh ec2-user@10.0.1.174 'bash /opt/tomcat8/bin/shutdown.sh'
                    ssh ec2-user@10.0.1.174 'bash /opt/tomcat8/bin/startup.sh'
                """
            }
           
        }
        }
    }
}