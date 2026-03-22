pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'JDK11'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/ankitjha100/MavenJenkinsPipeline.git'
            }
        }

        stage('Build') {
            steps {
                withEnv(["JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64"]) {
                    sh 'java -version'
                    sh 'mvn clean package'
                }
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar target/MyMavenApp-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
