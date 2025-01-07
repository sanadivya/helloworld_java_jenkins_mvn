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
                echo "Build succeeded!"
        }
        failure {
                echo "Build failed"
        }
    }
}
