pipeline {
  agent any

  options {
    buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
  }

  stages {
    Stage('Unit Tests'){
      steps {
        sh 'ant -f test.xml -v'
        junit 'reports/results.xml'
      }
    }
    stage('build'){
      steps {
        sh 'ant -f build.xml -v'
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'dist/*.jar', fingerprint: true
    }
  }
}
