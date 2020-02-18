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
                       }  
        stage('Publish') {
            steps {
                 nexusPublisher nexusInstanceId: '8630770A-04A05345-E3B371BA-5B01253F-CD6D2CA8', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/var/jenkins_home/workspace/simple-java-maven-app/target/my-app-1.0-SNAPSHOT.jar']], mavenCoordinate: [artifactId: 'simple-java-maven-app', groupId: 'org.jenkins-ci.main', packaging: 'jar', version: '1.01']]], tagName: '125'
                  } 
                        
        }
    }
}
