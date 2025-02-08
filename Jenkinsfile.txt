pipeline {
    agent { label 'agent1' }

    stages {
        stage('Build') {
            steps {
                script {
                  bat 'echo Starting Hello World Pipeline'
                  bat 'javac Hello.java'
                }
            }
        }

        stage('Execute Script') {
            steps {
                script {
                    bat 'java Hello'
                }
            }
        }
    }
}
