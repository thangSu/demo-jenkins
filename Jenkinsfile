pipeline{
    agent any 
    tools{
        maven 'maven3'
    }
    environment{
        PATH = "_path_of_bin:$PATH"
    }
    stages{
        stage('Git checkout'){
            steps{
               git 'https://github.com/thangSu/helloworld.git'
            }
        }
        stage("maven build"){
            steps{
                    sh 'mvn clean package'
            }
        }
    }
}