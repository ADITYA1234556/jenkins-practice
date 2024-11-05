pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'master', url: 'https://github.com/ADITYA1234556/jenkins-practice.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Build') {
            steps {
                echo 'Building app'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run tests directly since the test file is in the root
                sh 'python3 -m unittest test_app.py'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging the application...'
                sh 'zip -r app.zip app.py requirements.txt Procfile test_app.py'
                archiveArtifacts artifacts: 'app.zip', fingerprint: true
            }
        }
    }

    post {
        success {
        emailext( to: "adityanavaneethan98@gmail.com", subject: "Jenkins Build Successful: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}", body: "The build was successful! You can access it here: ${env.BUILD_URL}", attachLog: true)
        }
        failure {
        emailext( to: 'adityanavaneethan98@gmail.com', subject: 'Jenkins Build failed: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}', body: 'The build was failure! You can access it here: ${env.BUILD_URL}',attachLog: true)
        }
        unstable {
        emailext( to: 'adityanavaneethan98@gmail.com', subject: 'Jenkins Build unstable: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}', body: 'The build was unstable! You can access it here: ${env.BUILD_URL}',attachLog: true)
        }
    }

}
##