pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                echo "Building project..."
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                bat 'mvn test'
            }
        }

        stage('Release Checks') {
            when {
                branch 'release'
            }
            steps {
                echo "Running release checks..."
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
