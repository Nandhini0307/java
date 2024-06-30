pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository containing the Java code
                git 'https://github.com/Nandhini0307/java.git'
            }
        }
        stage('Compile') {
            steps {
                script {
                    // Define the Java home directory and update the PATH
                    def javaHome = tool name: 'jdk-22', type: 'JDK'
                    env.JAVA_HOME = javaHome
                    env.PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
                    
                    // Print Java version to verify the setup
                    sh 'java -version'
                }
                
                // Compile your Java code here
                sh 'javac sample.java'
            }
        }
        stage('Build') {
            steps {
                // Compile the Java code
                script {
                    def javaHome = tool name: 'jdk-22', type: 'JDK'
                     env.JAVA_HOME = javaHome
                    env.PATH = "${env.JAVA_HOME}/bin:${env.PATH}"
                }
                sh 'javac sample.java'
            }
        }
        stage('Test') {
            steps {
                // Run the Java application to verify it works
                sh 'java sample'
            }
        }
    }
}
