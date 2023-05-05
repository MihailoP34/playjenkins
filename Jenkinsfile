pipeline {
  agent {
    kubernetes {
      yaml '''
metadata:
  labels:
    some-label: some-label-value
    class: KubernetesDeclarativeAgentTest
spec:
  nodeSelector:
      kubernetes.io/os: windows
  containers:
  - name: jnlp
    image: jenkins/inbound-agent:nanoserver-1809
    env:
    - name: CONTAINER_ENV_VAR
      value: jnlp
  - name: docker-cli
    image: docker:rc-windowsservercore-1809
    env:
    - name: CONTAINER_ENV_VAR
      value: docker
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