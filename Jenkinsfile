pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
        PATH = "${env.NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your GitHub repo
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
                echo 'Building and running the app...'
                sh 'node index.js'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving JavaScript files as build artifacts...'
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