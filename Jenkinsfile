pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'javac app/Main.java'
            }
        }

        stage('Test/Run') {
            steps {
                sh 'java -cp app Main'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'app/*.class', fingerprint: true
            }
        }
        stage('Notify Slack') {
            steps {
                withCredentials([string(credentialsId: 'slack-webhook', variable: 'SLACK_WEBHOOK')]) {
                sh '''
                    curl -X POST -H 'Content-type: application/json' \
                    --data '{"text":"✅ Jenkins SUCCESS - PipeLine-JebariHouda - Build #${BUILD_NUMBER}"}' \
                    "$SLACK_WEBHOOK"
                '''
                }
            }
        }

    }
}
