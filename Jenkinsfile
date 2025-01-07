pipeline {
    agent any

    tools {
        maven 'Maven_3.9.9' // Name of the Maven configuration in Jenkins
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            cleanWs()
        }
        success {
                echo "Build succeeded!"
        }
        failure {
                echo "Build failed"
        }
    }
}
