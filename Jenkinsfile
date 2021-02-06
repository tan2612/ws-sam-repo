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
                withVault(configuration: [timeout: 60, vaultCredentialId: 'vault-token', vaultUrl: 'http://localhost:8200'
​], vaultSecrets: [[path: 'kv/muleSecret', secretValues: [[vaultKey: 'HArtifactId'], [vaultKey: 'HEnv'], [vaultKey: 'HPassword'], [vaultKey: 'HUsername'], [vaultKey: 'HVersion'], [vaultKey: 'HWorkerType']]]]) {
            bat "mvn clean package deploy -DmuleDeploy -Dmule.version=HVersion -Danypoint.username=HUsername -Danypoint.password=HPassword -Dcloudhub.env=HEnv -Dproject.artifactId=HArtifactId -Dcloudhub.workerType=HWorkerType"
            //sh 'docker login -u $username -p $password'
        }
                //bat "mvn clean package deploy -DmuleDeploy -Dmule.version=4.3.0 -Danypoint.username=ty2021 -Danypoint.password=tan/ANYPOINT20 -Dcloudhub.env=Sandbox -Dproject.artifactId=ws-sam2 -Dcloudhub.workerType=MICRO"
            }
        }
    }
}