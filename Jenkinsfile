pipeline {
  agent none
  stages {
    stage('Build and Test') {
      agent {
        node {
          label 'docker'
        }

      }
      steps {
        bat 'mvn -Dmaven.test.failure.ignore clean package'
        stash(name: 'build-test-artifacts', includes: ' **/target/surefire-reports/TEST-*.xml,target/*.jar')
      }
    }

    stage('Report & Publish') {
      steps {
        unstash 'build-test-artifacts'
      }
    }

  }
}