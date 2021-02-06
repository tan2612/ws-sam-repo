pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                //get code from repo
                git 'https://github.com/tan2612/ws-sam-repo.git'
                bat "mvn clean package"
            }
        }
        stage('Test'){
            steps {
                //get code from repo
                git 'https://github.com/tan2612/ws-sam-repo.git'
                bat "mvn clean test"
            }
        }
        stage('Deploy'){
            steps {
                //get code from repo
                git 'https://github.com/tan2612/ws-sam-repo.git'
                bat "mvn clean package deploy -DmuleDeploy -Dmule.version=4.3.0 -Danypoint.username=ty2021 -Danypoint.password=tan/ANYPOINT20 -Dcloudhub.env=Sandbox -Dproject.artifactId=ws-sam2 -Dcloudhub.workerType=MICRO"
            }
        }
    }
}