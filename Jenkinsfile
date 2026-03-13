pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from your Git repository
                git branch: 'main', url: 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Compile') {
            steps {
                script {
                    // Ensure Java is installed on Jenkins agent
                    sh 'javac -version'
                    // Compile all Java files in the repo
                    sh 'javac -d out $(find . -name "*.java")'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Replace 'MainClassName' with your actual main class name
                    sh 'java -cp out MainClassName'
                }
            }
        }
    }

    post {
        failure {
            echo 'Build failed. Please check the logs.'
        }
        success {
            echo 'Java program executed successfully!'
        }
    }
}
