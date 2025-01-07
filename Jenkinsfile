pipeline {
    agent any

    tools {
        maven 'MAVEN' // Name of the Maven configuration in Jenkins
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
            def timestamp = new Date().format("yyyyMMdd_HHmmss")
            archiveArtifacts artifacts: "**/target/*.jar", allowEmptyArchive: true, fingerprint: true
            archiveArtifacts artifacts: "target/helloworld-${timestamp}.jar", allowEmptyArchive: true, fingerprint: true
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
