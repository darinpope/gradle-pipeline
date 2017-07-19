pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './gradlew clean build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo `date`'
                input 'do you want to deploy?'
                sh 'echo `date`'
                sh 'zip gs-spring-boot.zip Procfile build/libs/gs-spring-boot-0.1.0.jar'
                sh 'aws s3 cp gs-spring-boot.zip s3://cb-dpope-apps/${BUILD_NUMBER}/gs-spring-boot.zip --profile cloudbees-ps'
                sh 'aws elasticbeanstalk create-application-version --application-name gradle-pipeline --version-label ${BUILD_NUMBER} --source-bundle S3Bucket="cb-dpope-apps",S3Key="${BUILD_NUMBER}/gs-spring-boot.zip" --profile cloudbees-ps'
                sh 'aws elasticbeanstalk update-environment --application-name gradle-pipeline --environment-name production --version-label ${BUILD_NUMBER} --profile cloudbees-ps'
            }
        }
    }
}
