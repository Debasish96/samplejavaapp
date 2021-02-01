pipeline {
  agent any
  stages {
    stage('compile') {
      steps {
        git 'https://github.com/lerndevops/samplejavaapp.git'
        sh '/opt/maven/apache-maven-3.6.3/bin/mvn compile'
        sleep 10
      }
    }

    stage('unit-test') {
      post {
        success {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        sh '/opt/maven/apache-maven-3.6.3/bin/mvn test'
      }
    }

    stage('package') {
      steps {
        sh '/opt/maven/apache-maven-3.6.3/bin/mvn clean package'
      }
    }

  }
}
