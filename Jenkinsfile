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
                        echo 'Starting frontend checks...'
                        script {
                            // Sleep for exactly 4 seconds natively in Jenkins
                            sleep time: 4, unit: 'SECONDS'
                            // Write the text report file natively
                            writeFile file: 'frontend_report.txt', text: 'Frontend Check Status: SUCCESS'
                        }
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Starting backend checks...'
                        script {
                            // Sleep for exactly 4 seconds natively in Jenkins
                            sleep time: 4, unit: 'SECONDS'
                            // Write the text report file natively
                            writeFile file: 'backend_report.txt', text: 'Backend Check Status: SUCCESS'
                        }
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
