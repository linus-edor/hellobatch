pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Build') {
      agent {
        node {
          label 'master'
        }

      }
      steps {
        withMaven(maven: 'M3') {
          sh 'mvn clean package'
        }

      }
    }
    stage('Results') {
      steps {
        junit(allowEmptyResults: true, testResults: '**/target/surefire-reports/TEST-*.xml')
        archiveArtifacts 'target/*.jar'
      }
    }
  }
}