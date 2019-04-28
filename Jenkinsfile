pipeline {
  agent any
  stages {
    stage('scm checout') {
      steps {
        git(url: 'https://github.com/Farden/spring-boot-eureka-zuul.git', branch: 'master', credentialsId: '723d978a-be56-4bef-a1a0-a6e9c95a4bba')
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
