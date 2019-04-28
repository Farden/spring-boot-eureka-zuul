pipeline {
  agent any
  stages {
    stage('scm checout') {
      steps {
        git(url: 'https://gitlab.com/spring-boot-appplication/spring-docker.git', branch: 'master', credentialsId: '0d3b8db6-1e6b-47d5-a8d6-c12754422241')
      }
    }
    stage('Build') {
        steps {
         withMaven(maven:'maven-3') {
            sh 'mvn package'
        }
      }  
    }
    stage('Sonar Static Analysis') {
        steps {
            withSonarQubeEnv('sonarqube server') {
                // Optionally use a Maven environment you've configured already
                withMaven(maven:'maven-3') {
                    sh 'mvn clean package sonar:sonar'
            }
        }
    }
}
