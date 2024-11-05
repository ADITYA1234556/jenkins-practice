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
}