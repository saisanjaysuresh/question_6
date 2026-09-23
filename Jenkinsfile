pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This pulls the latest code from the repository linked to the Jenkins job
                checkout scm
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Frontend Check') {
                    steps {
                        echo 'Running frontend script...'
                        // Use 'python' instead of 'python3' if running on a Windows Jenkins agent
                        sh 'python3 frontend_check.py'
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Running backend script...'
                        sh 'python3 backend_check.py'
                    }
                }
            }
        }

        stage('Archive Reports') {
            steps {
                echo 'Archiving report artifacts...'
                archiveArtifacts artifacts: 'frontend_report.txt, backend_report.txt', allowEmptyArchive: false
            }
        }
    }
}
