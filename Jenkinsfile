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

        stage('Uninstall Current Chrome') {
            steps {
                bat '''
                echo Uninstalling current Google Chrome
                chocko uninstall Google Chrome -y'''
            }
        }

        stage('Install Specific version of Chrome') {
            steps {
                bat '''
                echo Installing Google Chrome version %CHROME_VERSION%
                chocko install googlechrome --version=%CHROME_VERSION% -y --allow-downgrade --ignore-checksums'''
        }

        stage('Download and Install ChromeDriver') { 
            steps { 
                bat ''' echo Downloading ChromeDriver version %CHROMEDRIVER_VERSION% powershell -command "Invoke-WebRequest -Uri https://chromedriver.storage.googleapis.com/%CHROMEDRIVER_VERSION%/chromedriver_win32.zip -OutFile chromedriver.zip -UseBasicParsing" powershell -command "Expand-Archive -Path chromedriver.zip -DestinationPath ." powershell -command "Move-Item -Path .\\chromedriver.exe -Destination '%CHROME_INSTALL_PATH%\\chromedriver.exe' -Force" '''
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