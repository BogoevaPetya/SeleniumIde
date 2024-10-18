pipeline {
    agent any

    environment{
        CHROME_VERSION = '127.0.6533.73'
        CHROMEDRIVER_VERSION = '127.0.6533.73'
        CROME_INSTALL_PATH = 'C:\\Program Files\\Google\\Chrome\\Application'
        CHROMEDRIVER_PATH = '"C:\\Program Files\\Google\\Chrome\\Application\\chromedriver.exe"'
    }
    stages {
        stage('Checkout code') {
            steps {
                git branch: 'master', url: 'https://github.com/BogoevaPetya/SeleniumIde.git'
            }
        }

        stage('Set up .NET core') {
            steps {
                bat '''
                echo Installing .NET SDK 6.0
                chocko install dotnet-sdk -y --version=6.0.100'''
            }
        }

        // stage('Build project') {
        //     steps {
        //         bat 'dotnet build'
        //     }
        // }
        // stage('Execute tests') {
        //     steps {
        //         bat 'dotnet test'
        //     }
        // }
    }
}