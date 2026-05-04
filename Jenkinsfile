pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Neha0620/Contact-Manager.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            // Publish JUnit test results in Jenkins
            junit 'target/surefire-reports/*.xml'
        }

        success {
            echo "Build and Tests SUCCESS ✔"
        }

        failure {
            echo "Build FAILED ❌ Check logs"
        }
    }
}
