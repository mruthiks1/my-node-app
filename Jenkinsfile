pipeline {
    agent any

    environment {
        // Name must match your NodeJS installation in Jenkins Global Tool Configuration
        NODEJS_HOME = tool name: 'NodeJS', type: 'NodeJSInstallation'
        PATH = "${env.NODEJS_HOME}\\bin;${env.PATH}"
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
                bat 'npm install'
            }
        }

        stage('Build & Run') {
            steps {
                echo 'Running the app...'
                // Use start /B to run in background if needed
                bat 'node index.js'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving JavaScript files...'
                archiveArtifacts artifacts: '**\\*.js', fingerprint: true
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