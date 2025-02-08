pipeline {
    agent { label 'agent-anant1' }  // Use the specific agent label

    tools {
        // Check if this is a Linux agent
        if (isUnix()) {
            git '/usr/bin/git'  // Path for Git on Linux agents
        } else {
            git 'C:/Program Files/Git/bin/git.exe'  // Path for Git on Windows agents
        }
    }

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

