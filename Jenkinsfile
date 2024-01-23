pipeline {

  parameters { 
    string(name: 'AGENT_LABEL', defaultValue: "CM_CAI-W20170", description: 'node/agent to run the pipeline on') 
  }
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {
    stage('Build') {
      steps {
         echo "hello world"
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
