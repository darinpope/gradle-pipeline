pipeline {
    agent any
    stages {
        stage('Example Build') {
            steps {
                sh 'echo Hello World'
                sh './gradlew clean build'
            }
        }
    }
}
