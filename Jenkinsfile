pipeline {
  agent {
    kubernetes {
      yaml '''
metadata:
  labels:
    some-label: some-label-value
    class: KubernetesDeclarativeAgentTest
spec:
  containers:
  - name: jnlp
    env:
    - name: CONTAINER_ENV_VAR
      value: jnlp
'''
    }
  }
  stages {
    stage('Run pls') {
      steps {
        container('jnlp') {
          powershell 'docker --version'
        }
      }
    }
  }
}