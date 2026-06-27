pipeline{
    agent any
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
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('artifact'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
        stage('deploy to tomcat'){
            steps{
                sh 'cp target/*.jar /opt/tomcat/webapps/'
            }
        }
    }
}