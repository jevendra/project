pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the web application...'
                sh 'test -f index.html'
                sh 'test -f style.css'
                sh 'test -f script.js'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic application tests...'
                sh 'grep -q "CI/CD Demo Web App" index.html'
                sh 'grep -q "addEventListener" script.js'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying web application...'
                sh 'mkdir -p deploy'
                sh 'cp index.html style.css script.js deploy/'
                echo 'Deployment completed successfully.'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline completed successfully! 🚀'
        }
        failure {
            echo 'CI/CD Pipeline failed. Check the console output.'
        }
    }
}
