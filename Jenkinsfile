pipeline{
    agent any
    triggers {
        pollSCM('H/2 * * * *')
    }
    stages{
        stage('github validation'){
          steps{
                 git url: 'https://github.com/SriVyshnaviP/addressbook-cicd-project.git'
          }
        }
        stage('compiling the code'){
          steps{
                 sh 'mvn compile'
          }
        }
        stage('testing the code'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa of the code'){
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage("deploy the project on tomcat"){
            steps{
                sh "sudo cp /var/lib/jenkins/workspace/pipeline-job/target/addressbook.war /root/apache-tomcat-9.0.111/webapps"
            }
        }
    }
}
