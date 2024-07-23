pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Clean and compile the project
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                // Run the tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy step - customize this to your needs
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            // Archive test results and build artifacts
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }

        success {
            echo 'Build was successful!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}

