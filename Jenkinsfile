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
                            sleep time: 4, unit: 'SECONDS'
                            writeFile file: 'frontend_report.txt', text: 'Frontend Check Status: SUCCESS'
                        }
                    }
                }
                stage('Backend Check') {
                    steps {
                        echo 'Starting backend checks...'
                        script {
                            sleep time: 4, unit: 'SECONDS'
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
