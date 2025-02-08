pipeline {
    agent { label 'agent-anant1' }  // Use the specific agent label

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Checkout your repository
            }
        }

        stage('Build') {
            steps {
                script {
                    // For Windows agent
                    if (!isUnix()) {
                        bat 'echo Starting Hello World Pipeline'
                        bat 'javac Hello.java'  // Compile the Java file
                    }
                    // For Linux agent
                    else {
                        sh 'echo Starting Hello World Pipeline'
                        sh 'javac Hello.java'  // Compile the Java file
                    }
                }
            }
        }

        stage('Execute Script') {
            steps {
                script {
                    // For Windows agent
                    if (!isUnix()) {
                        bat 'java Hello'  // Run the compiled Java file
                    }
                    // For Linux agent
                    else {
                        sh 'java Hello'  // Run the compiled Java file
                    }
                }
            }
        }
    }
}
