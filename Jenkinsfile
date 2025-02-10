pipeline {
    agent { label 'agent-anant1' }

    environment {
        APP_ENV = 'development' // Change to 'production' for production builds
    }

    stages {
        stage('Clone Repository') {
            steps {
                sh 'rm -rf docker-build || true'
                sh 'git clone -b main https://github.com/Anant-1209/docker-build.git'
                echo "Cloned..."
            }
        }

        stage('Set Environment') {
            steps {
                script {
                    if (env.APP_ENV == 'production') {
                        echo "Running Production Build"
                    } else {
                        echo "Running Development Build"
                    }
                }
            }
        }

        stage('Compile & Run Java Programs in Parallel') {
            parallel {
                stage('Task 1 - Compile & Run Java Program 1') {
                    steps {
                        sh '''
                            cd docker-build
                            javac Program1.java
                            java Program1
                        '''
                    }
                }
                stage('Task 2 - Compile & Run Java Program 2') {
                    steps {
                        sh '''
                            cd docker-build
                            javac Program2.java
                            java Program2
                        '''
                    }
                }
            }
        }

        stage('Archive Build Outputs') {
            steps {
                archiveArtifacts artifacts: 'docker-build/*.class', fingerprint: true
                echo "Archived compiled .class files"
            }
        }

        stage('Workspace Cleanup') {
            steps {
                //cleanWs()
                echo "Workspace cleaned up"
            }
        }
    }
}
