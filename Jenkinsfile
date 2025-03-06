@Library("Shared") _

pipeline {
    agent any

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                echo "This is cloning the project"
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/KhadkaBibek/django-notes-app.git']])
               
                
            }
        }
        stage('Build') {
            steps {
                echo "This is building the project"
                sh "docker build -t notes-app:latest ."
                
            }
        }
        stage('Push to DockerHub') {
            steps {
                
                script{
                    docker_push("notes-app","latest","khadkabibek4")
                }
            }
        }
        
    }
}
