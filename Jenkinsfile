pipeline {
    agent any

    stages {

        stage('Backend - Install') {
            steps {
                echo 'Installing backend dependencies...'

                dir('backend') {
                    bat 'npm ci'
                }
            }
        }

        stage('Backend - Test') {
            steps {
                echo 'Running backend tests...'

                dir('backend') {
                    bat 'npm test'
                }
            }
        }

        stage('Backend - Build') {
            steps {
                echo 'Building backend...'

                dir('backend') {
                    bat 'npm run build --if-present'
                }
            }
        }

        stage('Frontend - Install') {
            steps {
                echo 'Installing frontend dependencies...'

                dir('frontend') {
                    bat 'npm ci'
                }
            }
        }

        stage('Frontend - Test') {
            steps {
                echo 'Running frontend tests...'

                dir('frontend') {
                    bat 'npm test'
                }
            }
        }

        stage('Frontend - Build') {
            steps {
                echo 'Building frontend...'

                dir('frontend') {
                    bat 'npm run build'
                }
            }
        }
    }

    post {
        success {
            echo '======================================'
            echo 'NutriFlow CI Pipeline Successful!'
            echo 'Install, Test and Build completed.'
            echo '======================================'
        }

        failure {
            echo '======================================'
            echo 'NutriFlow CI Pipeline Failed!'
            echo 'Check the failed stage in Jenkins.'
            echo '======================================'
        }

        always {
            echo 'Jenkins pipeline execution completed.'
        }
    }
}