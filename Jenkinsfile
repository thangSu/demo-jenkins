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
                } 
            }
        }
    }
}