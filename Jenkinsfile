pipeline {
  agent any

  options {
    buildDiscarder(logRotator(numTokeepStr: '2', artifactNumTokeeperStr: '1'))
  }

  stages {
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
