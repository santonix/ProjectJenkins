pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '3'))
    }
    tools {
        jdk 'jdk8'
        maven 'maven3'
    }
    triggers {
        cron('* * * * *')
    }
    stages {
        stage('checkout') {
            steps {
                git branch: 'feature1', credentialsId: 'dockerhub-credentials', url: 'git@github.com:santonix/ProjectJenkins.git'
            }
        }
        stage('build && test') {
            steps {
                sh 'mvn clean install && mvn clean verify '
            }
        }
    }
}
