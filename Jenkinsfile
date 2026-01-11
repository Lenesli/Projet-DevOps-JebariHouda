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
                bat 'javac app\\Main.java'
            }
        }

        stage('Test/Run') {
            steps {
                bat 'java -cp app Main'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'app/*.class', fingerprint: true
            }
        }
    }
}
