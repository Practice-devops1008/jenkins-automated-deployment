pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Configure this job with your GitHub repository URL.
                checkout scm
            }
        }

        stage('Build WAR') {
            steps {
                sh 'mvn -B clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/sample.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build completed. Configure a secured Tomcat deployment stage in Jenkins to deploy target/sample.war.'
        }
        failure {
            echo 'Build failed. Review the console output above to identify the failing stage.'
        }
    }
}
