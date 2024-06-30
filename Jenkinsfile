pipeline {
    agent any

    tools {
        // Define the Maven tool to be used
        maven 'apache-maven-3.9.8' // This should match the name given in the tool configuration
    }

    environment {
        // Define the JDK to be used
        JAVA_HOME = tool name: 'jdk-22', type: 'JDK' // Adjust this according to your JDK configuration
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the Git repository
                git 'https://github.com/Nandhini0307/java.git'
            }
        }

        stage('Build') {
            steps {
                // Clean and build the Maven project
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                // Run Maven tests
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Package the application
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            // Archive the built artifacts
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
        always {
            // Publish test results
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
