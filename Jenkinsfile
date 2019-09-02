pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo "hello world"'
            }
        }
	stage('Sonarqube') {
    environment {
        scannerHome = tool 'My Scanner'
    }
    steps {
        withSonarQubeEnv('My SonarQube Server') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
    }
}
