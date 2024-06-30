pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Nandhini0307/java.git'
            }
        }
        stage('Build') {
            steps {
                sh 'javac sample.java'
            }
        }
        stage('Run') {
            steps {
                sh 'java sample'
            }
        }
    }
}
