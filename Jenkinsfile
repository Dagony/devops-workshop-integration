pipeline {
    agent {
        dockerfile {
            filename 'Dockerfile.build'
        }
    }
    stages {
        stage('prepare') {
            steps {
                git 'https://github.com/Dagony/devops-workshop-integration.git'

            }
        }
        stage('build') {
            steps {
                sh "mvn' -Dmaven.test.failure.ignore clean package"
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