
pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    options {
        timestamps()
        disableConcurrentBuilds()
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Java application'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Java application'
                sh 'mvn clean compile'
            }
        }

        stage('Unit Testing') {
            steps {
                echo 'Executing unit tests'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Generating application JAR'
                sh 'mvn package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar',
                                 fingerprint: true
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true,
                  testResults: 'target/surefire-reports/*.xml'
        }

        success {
            echo 'BUILD SUCCESSFUL'
        }

        failure {
            echo 'BUILD FAILED - Check Jenkins console logs'
        }

        cleanup {
            echo 'Pipeline execution completed'
        }
    }
}
