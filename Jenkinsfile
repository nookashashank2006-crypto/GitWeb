pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {

        stage('clean') {
            steps {
                bat "mvn clean"
            }
        }

        stage('install') {
            steps {
                bat "mvn install"
            }
        }

        stage('test') {
            steps {
                bat "mvn test"
            }
        }

        stage('package') {
            steps {
                bat "mvn package"
            }
        }
    }

    post {
        success {
            emailext(
                to: 'nookashashank2006@gmail.com',
                subject: "Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build ${env.BUILD_NUMBER} completed successfully.\n\n${env.BUILD_URL}"
            )
        }

        failure {
            emailext(
                to: 'nookashashank2006@gmail.com',
                subject: "Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build ${env.BUILD_NUMBER} failed.\n\n${env.BUILD_URL}"
            )
        }
    }
}
