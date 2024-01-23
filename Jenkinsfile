pipeline {
  agent {label '${AGENT_LABEL}'}
  parameters { 
    string(name: 'AGENT_LABEL', defaultValue: 'CM_CAI-W20170', description: 'node/agent to run the pipeline on') 
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
        sh './gradlew clean check --no-daemon'
      }
    }
  }
  post {
    always {
        junit(
          allowEmptyResults: true, 
          testResults: '**/build/test-results/test/*.xml'
        )
    }
  }
}
