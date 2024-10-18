pipeline {
    agent any

    environment{
        CHROME_VERSION = '127.0.6533.73'
        CHROMEDRIVER_VERSION = '127.0.6533.73'
        CROME_INSTALL_PATH = 'C:\\Program Files\\Google\\Chrome\\Application'
        CHROMEDRIVER_PATH = '"C:\\Program Files\\Google\\Chrome\\Application\\chromedriver.exe"'
    }
    stages {
        stage('Build project') {
            steps {
                bat 'dotnet build'
            }
        }
        stage('Execute tests') {
            steps {
                bat 'dotnet test'
            }
        }
    }
}