pipeline {
    agent { label 'agent-anant1' }  // Specify the agent label for Windows machine

    tools {
        git 'default'  // Reference the Git tool configured in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Checkout your repository using Git
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
