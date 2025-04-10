pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'NodeJS' // Matches the name from Global Tool Configuration
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/RajputMahendra123/NodeJS_CI_CD.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install' // Install Node.js dependencies (no dependencies needed for this example)
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build' // Placeholder build step
            }
        }

        stage('Test') {
            steps {
                sh 'npm test' // Runs the test script, which executes index.js
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                sh 'npm run deploy' // Placeholder deploy step
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed! Deployment aborted.'
        }
        success {
            echo 'Pipeline succeeded! Application deployed.'
        }
    }
}