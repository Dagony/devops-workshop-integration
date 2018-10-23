pipeline {
    agent { docker { image 'maven:3.3.3' } }
    stages {
        stage('prepare') {
            steps {
                git 'https://github.com/Dagony/devops-workshop-integration.git'

                mvnHome = tool 'M3'
            }
        }
        stage('build') {
            steps {
                sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
            }
        }
        stage('results') {
            steps {
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts 'target/*.jar'
            }
        }
    }
}