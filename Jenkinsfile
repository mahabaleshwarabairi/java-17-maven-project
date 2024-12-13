pipeline {
    agent any

    // Define environment variables (optional)
    environment {
        MAVEN_HOME = '/usr/local/maven' // Update this path to match your Maven installation
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling code from GitHub...'
                // Or use explicit Git details:
                git branch: 'main', url: 'https://github.com/felix-seifert/java-17-maven-project.git'
                sh 'ls -l'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project with Maven...'
                sh "${MAVEN_HOME}/bin/mvn clean install"
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests with Maven...'
                sh "${MAVEN_HOME}/bin/mvn test"
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging the application...'
                sh "${MAVEN_HOME}/bin/mvn package"
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed. Please check the logs.'
        }
        always {
            echo 'Cleaning up workspace...'
            //cleanWs() Cleans up the workspace
        }
    }
}

