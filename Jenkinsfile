
pipeline {
    agent any

    stages {
        stage('Download_Loans') {
            steps {
                echo 'Downloading Maven project...'
                git branch: 'loans',
                    url: 'https://github.com/brajakumar1234/maven9.git'
            }
        }

        stage('Build_Loans') {
            steps {
                echo 'Building Maven application...'
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Loans application build completed successfully!'
        }
        failure {
            echo 'Loans application build failed. Check console output.'
        }
    }
}
