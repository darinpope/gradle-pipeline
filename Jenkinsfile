pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo Hello World'
                sh './gradlew clean build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo deploy'
            }
        }
    }
}
