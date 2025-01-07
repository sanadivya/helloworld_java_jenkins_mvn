pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '''
                mvn clean install
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                mvn test
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            cleanWs()
        }
        success {
                 subject: "Build succeeded!"
        }
        failure {
                 subject: "Build failed"
        }
    }
}
