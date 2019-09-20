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
             environmet {
                TOMCAT_URL = 'c_tomcat'
            }
            steps {
                sh 'curl -s --upload-file ${WORKSPACE}/target/*.war "http://${TOMCAT_URL}:8080/manager/text/deploy?path=/web&update=true"'
            }
        }
    }
}
