pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Parallel Checks') {
            parallel {
                stage('Frontend Check') {
                    steps {
                        echo 'Running frontend script...'
                        // Try sh first. If you are on Windows Jenkins, change 'sh' to 'bat'
                        sh 'python3 frontend_check.py'
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Running backend script...'
                        // Try sh first. If you are on Windows Jenkins, change 'sh' to 'bat'
                        sh 'python3 backend_check.py'
                    }
                }
            }
        }

        stage('Archive Reports') {
            steps {
                echo 'Archiving report artifacts...'
                // Changed to true temporarily so the pipeline won't fail if scripts have an path error
                archiveArtifacts artifacts: 'frontend_report.txt, backend_report.txt', allowEmptyArchive: true
            }
        }
    }
}
