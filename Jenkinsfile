pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage('git clone'){
            steps{
                git branch: 'main', url: 'https://github.com/rahu08910-droid/SpringFormApp.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('artifact'){
            steps{
                archiveArtifacts artifacts: 'target/*.war'
            }
        }
        stage('deploy to tomcat'){
            steps{
                sh 'cp target/*.war /opt/tomcat/webapps/'
            }
        }
    }
}
