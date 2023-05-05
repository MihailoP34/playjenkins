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
        cmd "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('jnlp') {
          cmd 'echo MAVEN_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          cmd 'mvn -version'
        }
      }
    }
  }
}