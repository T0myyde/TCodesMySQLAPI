pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'test 1'
            }
        }
        stage('Build') {
            steps {
                echo 'test 2'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
