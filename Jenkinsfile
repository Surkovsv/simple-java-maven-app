pipeline {
    agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        stage('Publish') {
            steps {
                 curl -v -u jenkins:123456 --upload-file pom.xml http://nexus:8081/repository/maven-releases/
        }
    }
}
