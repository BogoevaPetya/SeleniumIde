pipeline {
    agent any
    stages {
        stage('Build project') {
            steps {
                bat 'dotnet build'
            }
        }
        stage('Execute Tests') {
            steps {
                bat 'dotnet test'
            }
        }   
    }
}