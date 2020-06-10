pipeline {
    agent any
    
    environment{
        PATH = "/opt/maven/apache-maven-3.6.3/bin:$PATH"
    }
    
    stages {
        //def mvnHome
        stage('SCM checkout') {
            steps {
                echo 'Git checkout'
                git 'https://github.com/AishwaryaDevOps/hello-world.git'
            }
        }
        stage('Build Package') {
            steps {
                echo 'Maven build package'
                //def mvnHome = tool name: 'M2_HOME', type: 'maven'
                sh "mvn clean package"
            }
        }
        stage('Deploy war'){
            steps {
                echo 'deploy war'
                sshagent(['tomcat_cred']) {
                sh 'scp -o StrictHostKeyChecking=no webapp/target/*.war ec2-user@13.232.102.250:/opt/tomcat/webapps'
              // sh 'ssh -o StrictHostKeyChecking=no -l cloudbees 13.126.142.10 uname -a'
                 }
            }
        }
    }
}
