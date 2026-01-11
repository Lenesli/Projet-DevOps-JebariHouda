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
    }
}
