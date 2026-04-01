pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out Git repository...'
                git branch: 'main', url: 'https://github.com/mruthiks1/my-node-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Node.js dependencies...'
                sh 'npm install'
            }
        }

        stage('Build & Run') {
            steps {
                echo 'Running the app...'
                sh 'node index.js'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving JavaScript files...'
                archiveArtifacts artifacts: '**/*.js', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
