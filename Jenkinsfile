pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /home/ubuntu/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn clean package' 
            }
        }
        stage('deploy') {
             steps {
                sh 'cp **/*.war vigilant_mayer:/opt/tomcat/webapps'
            }  
        }
    }
}
