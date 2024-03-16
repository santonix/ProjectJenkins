pipeline  {
    agent any
    options {
       buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '3')
    }
    tools {
      jdk 'jdk17'
      maven 'maven3'
    }
    triggers {
      cron '* * * * * '
    }


    stages{
        stage ('checkout')
          steps {
            git branch: 'feature1', credentialsId: 'dockerhub-credentials', url: 'git@github.com:santonix/ProjectJenkins.git'
          }

        stage ('build && test') {
          steps {
            sh 'mvn clean verify -DskipITs=true' 
          }

        }  
    }
}
