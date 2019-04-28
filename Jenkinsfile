pipeline {
  agent any
  stages {
    stage('scm checout') {
      steps {
         git(url: 'https://github.com/Farden/spring-boot-eureka-zuul.git', branch: 'master', credentialsId: 'github')
      }
    }
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'mvn clean'
          }
        }
        stage('clean') {
          steps {
            sh 'mvn clean'
          }
        }
        stage('compile') {
          steps {
            sh 'mvn compile'
          }
        }
        stage('package') {
          steps {
            sh 'mvn package'
          }
        }
      }
    }
  }
}

        
