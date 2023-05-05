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
  - name: docker-cli
    image: docker:rc-windowsservercore-1809
    env:
    - name: CONTAINER_ENV_VAR
      value: jnlp
'''
    }
  }
  stages {
    stage('Run pls') {
      steps {
        container('docker-cli') {
          powershell 'docker --version'
        }
      }
    }
  }
}