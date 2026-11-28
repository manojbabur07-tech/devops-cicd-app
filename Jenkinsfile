
pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    options {
        timestamps()
        disableConcurrentBuilds()
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Java application'
                checkout scm
            }
        }

        stage('Verify Java and Maven') {
            steps {
                echo 'Checking Java and Maven versions'
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Java application'
                sh 'mvn -B clean compile'
            }
        }

        stage('Unit Testing') {
            steps {
                echo 'Executing unit tests'
                sh 'mvn -B test'
            }
        }

        stage('Package') {
            steps {
                echo 'Generating application JAR'
                sh 'mvn -B package'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving generated JAR'
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

pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    options {
        timestamps()
        disableConcurrentBuilds()
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out Java application'
                checkout scm
            }
        }

        stage('Verify Java and Maven') {
            steps {
                echo 'Checking Java and Maven versions'
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Java application'
                sh 'mvn -B clean compile'
            }
        }

        stage('Unit Testing') {
            steps {
                echo 'Executing unit tests'
                sh 'mvn -B test'
            }
        }

        stage('Package') {
            steps {
                echo 'Generating application JAR'
                sh 'mvn -B package'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving generated JAR'
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
